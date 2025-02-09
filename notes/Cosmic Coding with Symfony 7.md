---
title: Cosmic Coding with Symfony 7
created: '2025-01-15T12:16:48.833Z'
modified: '2025-01-16T15:12:17.294Z'
---

# Cosmic Coding with Symfony 7

https://symfonycasts.com/screencast/symfony/resume

## Pomodoros 🍅

15.01.2025 🍅🍅🍅🍅
16.01.2025 🍅🍅

## Notes

Install via DDEV:

```
mkdir my-symfony-site && cd my-symfony-site
ddev config --project-type=symfony --docroot=public
ddev start
ddev exec symfony check:requirements
ddev exec symfony new starshop
# move to main folder
ddev exec 'rsync -rltgopD starshop/ ./ && rm -rf starshop'

ddev launch
```

Symfony recipes: https://github.com/symfony/recipes/blob/flex/main/RECIPES.md, use aliases like `ddev composer require cs-fixer-shim`

- adds gitignore, config files, etc. + symfony.lock
- commands: ddev exec ./vendor/bin/php-cs-fixer

- `ddev composer require twig` 

- config/bundles.php - aktivieren, aber macht recipes package automatisch; config/packages/twig.yaml

- `ddev composer require debug`
- `ddev exec ./bin/console debug:router` - shows all available routes, `ddev exec ./bin/console debug:twig`

```
use Symfony\Bundle\FrameworkBundle\Controller\AbstractController;
use Symfony\Component\HttpFoundation\Response;
use Symfony\Component\Routing\Attribute\Route;
```

- Serializer for JSON output: `ddev composer require serializer` (automatically hooks into  `return $this->json($starships);`) 

### Most important concept: Services

- show all `ddev exec ./bin/console debug:container`
- Nutzung in PHP via $this->container->get('serializer') u.a., siehe 

```
  protected function json(mixed $data, int $status = 200, array $headers = [], array $context = []): JsonResponse
    {
        if ($this->container->has('serializer')) {
            $json = $this->container->get('serializer')->serialize($data, 'json', array_merge([
```

- "Bundles give us services" - and services are tools
- Autowirable types, e.g. for logging: `ddev exec ./bin/console debug:autowiring log`

```
 Describes a logger instance.
 Psr\Log\LoggerInterface - alias:monolog.logger
 Psr\Log\LoggerInterface $cacheLogger - alias:monolog.logger.cache
 Psr\Log\LoggerInterface $consoleLogger - alias:monolog.logger.console
 ...
 ```

```
 use Psr\Log\LoggerInterface;
 // ...
    dd($logger);
```

```
$logger->info('starships retrieved');
```

For HTTP, you can see logs via Debug toolbar. For REST API, you can navigate to https://my-symfony-site.ddev.site/_profiler which has the latest requests and you can see the logs there. 💡

Use autowiring:

```
    public function __construct(private LoggerInterface $logger) {}

    public function findAll(): array
    {
        $this->logger->info('Starshiiiips ...');
```

Services can be used in constructor as well as in method arguments.

### Routes

```
#[Route('/api/starships/{id<\d+>}', methods: ['GET'])]
    public function get(int $id): Response
```

Prefix every route automatically

```
#[Route('/api/starships')]
class StarshipApiController extends AbstractController

#[Route('', methods: ['GET'])]
    public function getCollection(StarshipRepository $repository): Response
```

See all routes: `ddev exec bin/console debug:router`

Throw 404s (or else):

```
if (!$starship) {
            throw $this->createNotFoundException('Starship not found');
        }
```

### Add name keys to link pages

```
#[Route('/starships/{id<\d+>}', name: 'app_starship_show')]
    public function show(int $id, StarshipRepository $repository): Response
```
```
<a href="{{ path('app_starship_show', {
                    id: myShip.id
                }) }}">{{ myShip.name }}</a>
```

### CSS & JS with Asset Mapper

- public/ folder for static files, but:
- https://symfony.com/doc/current/frontend/asset_mapper.html 

```
ddev composer require symfony/asset-mapper
```

Installs / adds to base.html.twig

```
   {% block javascripts %}
            {% block importmap %}{{ importmap('app') }}{% endblock %}
        {% endblock %}
```

Files: `/assets`

```
ddev exec php bin/console debug:asset
```

### Images

Images, asset mapper takes care of "Automatic Asset Versioning" by hashes

```
ddev composer require symfony/asset
```

```
<img src="{{ asset('images/starshop-logo.png') }}" alt="Starshop Logo">
```

Generates: 
```
https://my-symfony-site.ddev.site/assets/images/starshop-logo-3VMCiho.png
```

### Tailwind

- `ddev composer require symfonycasts/tailwind-bundle`
- `ddev exec ./bin/console tailwind:init`
- `ddev exec ./bin/console tailwind:build -w`

This is without nodejs

> This bundle makes it easy to use Tailwind CSS with Symfony's AssetMapper Component (no Node.js required!).

https://symfony.com/bundles/TailwindBundle/current/index.html

Usage with Webpack Encore: https://tailwindcss.com/docs/guides/symfony

### Enums

```
<?php
namespace App\Model;
enum StarshipStatusEnum: string
{
    case WAITING = 'waiting';
    case IN_PROGRESS = 'in progress';
    case COMPLETED = 'completed';
}
```

```
new Starship(
                1,
                'USS LeafyCruiser (NCC-0001)',
                'Garden',
                'Jean-Luc Pickles',
                StarshipStatusEnum::IN_PROGRESS
            ),
```

Use in Twig via `.value`:

```
<p class="uppercase text-xs text-nowrap">{{ ship.status.value }}</p>
```

#### Dynamic images based on Enum

```
public function getStatusImageFilename(): string
    {
        return match ($this->status) {
            StarshipStatusEnum::WAITING => 'images/status-waiting.png',
            StarshipStatusEnum::IN_PROGRESS => 'images/status-in-progress.png',
            StarshipStatusEnum::COMPLETED => 'images/status-complete.png',
        };
    }
```
Usage in Twig (with bit of automatic, Twig resolves Getter automatically):

```
<img class="h-[83px] w-[84px]" src="{{ asset(ship.statusImageFilename) }}" alt="Status: {{ ship.statusString }}">
```

### Stimulus JavaScript

- https://stimulus.hotwired.dev/, last released August 7th 2023
- JS -> connect HTML to JS Controller
- https://symfony.com/bundles/StimulusBundle/current/index.html 

### Turbo - SPA

- https://symfony.com/bundles/ux-turbo/current/index.html, Current version: 8.0.11 — released Oct 15, 2024

> Symfony UX Turbo is a Symfony bundle integrating the Hotwire Turbo library in Symfony applications. It is part of the Symfony UX initiative.

> Symfony UX Turbo allows having the same user experience as with Single Page Applications but without having to write a single line of JavaScript!
 
- automatically activated when we use Stimulus, page loads are intercepted and loaded via Ajax (feels faster than normal page load)

- Turbo also loads a page when you hover a link (similiar to SvelteKit, etc.), https://turbo.hotwired.dev/handbook/drive
  - https://turbo.hotwired.dev/handbook/drive#prefetching-links-on-hover

### Maker Bundle

- `ddev composer require symfony/maker-bundle --dev`

- create custom command `ddev exex ./bin/console make:command`

### Twig Hints

- `parent()` extend content of block without overriding it https://twig.symfony.com/doc/3.x/functions/parent.html

## Questions

- How to use php-cs-fixer with DDEVs PHP version? 
- symfony.lock ?

- [ ] Use tailwind with Vite instead of Webpack Encore? https://symfony-vite.pentatrion.com/ or something else?


