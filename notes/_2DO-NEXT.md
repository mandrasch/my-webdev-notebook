---
title: _2DO-NEXT
created: '2022-04-16T11:38:33.355Z'
modified: '2022-11-14T18:17:02.076Z'
---

# _2DO-NEXT

## Personal stack

- WordPress (open source & dynamic community)
- (Headless) Statamic + SvelteKit / others
  - [ ] https://statamictutorials.com/course/how-to-deploy-statamic/episode/0
- CraftCMS - very stable projects

- Tailwind
- 

## Next:

=> SvelteKit SSR => try/catch for fetch to see what's going or (use own api for time() on manitu?)

=> SvelteKit SSR demo project for showcase portfolio? (public 2 lake, public hike, etc.?)

-> Find reliable full stack approaches?
-> OER: Beats Biblionetz für OERhörnchen abbilden?
-> Public Transport Hikes / Bahn Zum See (Solo project, markdown is fine, what about images?)

-> the client dashboard is always the challenge?

- [ ] Vue as addition to Svelte Skills "needed"?

## SvelteKit

- [ ] Learn more about SSR hosting, build real sites with it
- [ ] Understand Netlify CMS and GDPR-compatible hosting https://www.youtube.com/watch?v=Pz-kQJxZx3w

## WordPress

- [ ] Roots Sage + Svelte / Vue Components

## Typo3 

- [ ] Use Svelte/Vue inside typo3 via API

## CraftCMS

- [ ] Deploy article dev.to part II, add deployer pipeline and test updates

- [ ] Real World Craft CMS Course https://craftquest.io/courses/real-world-craft-cms
- [ ] CraftCMS Deployment (Deployer / SSH+git+composer?) https://github.com/mandrasch/train-to-lake-craftcms, https://github.com/thomasbendl/craft4-ddev-vite-blueprint, https://www.mitrais.com/news-updates/how-to-create-ci-cd-with-github-action-and-laravel/
https://git.typo3.org/services/demo.typo3.org/site/-/blob/main/.gitlab-ci.yml 

- Skills: 
  - [ ] Tailwind Crash Course (+ Design System? https://www.youtube.com/watch?v=cZc4Jn5nK3k)
  - [ ] Typescript Crash Course
  - [ ] SvelteKit + Tailwind + TypeScript? https://tailwindcss.com/docs/guides/sveltekit

- Side project
  - [ ] ScreenreadThis: Convert to SvelteKit SSR project
  - [ ] Bootstrap5 + vite + CraftCMS? (train2lake?)


<hr>

Screenreader Remote Control:

- https://www.youtube.com/watch?v=Oz4CBHrxMMs
- https://github.com/raghavk92/Kontroller/issues/15

**NeXT: BahnZumSee + CraftCMS Learning Project**

1. BahnZumSee
- CraftCMS Prototype or SvelteKit Prototype or Nuxt Prototype?
- Both?
- Headless? 
- Open Source would be much cooler for projects like these?
  - Like Bedrock + WPGraphQL + ACF or WPGraphQL + Pods (https://docs.pods.io/tutorials/best-practices-for-pods-deployment/)
  - t3 https://extensions.typo3.org/extension/headless, https://github.com/TYPO3-Headless/nuxt-typo3, etc.?
  - GetCockpit v2? https://twitter.com/getcockpit/status/1554060611998433280 v2

2.CraftCMS test project: _______________________

- CraftCMS
- CraftCMS + Svelte
  - https://nystudio107.com/blog/using-vite-js-next-generation-frontend-tooling-with-craft-cms
  - https://blog.galaxyweblinks.com/craft-cms-building-the-frontend-of-a-website-using-twig-and-graphql/
  - https://github.com/D3strukt0r/CraftCMS-Svelte-Blueprint
- Sprig Reactivity Twig, like Laravel Livewire? https://putyourlightson.com/sprig?s=09
  - https://www.youtube.com/watch?v=DJqdF7kYgjE
  - https://putyourlightson.com/sprig/videos?s=09#sprigboard
  - https://blog.ohheybrian.com/2022/06/moving-from-svelte-to-htmx/?s=09 
- (Blitz https://plugins.craftcms.com/blitz)


<hr>

=> Deployer Statamic auf Ploi ausprobieren ... https://lorisleiva.com/deploy-your-laravel-app-from-scratch/deploy-using-ploi + https://www.youtube.com/watch?v=Dsld-2iHv2k
- https://statamic.dev/tips/zero-downtime-deployments#understanding-zero-downtime-deployment-file-structure


=> Statamic deploy with deployer and git-automation on manitu, https://github.com/mandrasch/statamic-deployer-test
  => document installation & setup

  => erstmal mit sftp lösen?! deployer auf mittwald dann machen next week ...

###  ! https://statamictutorials.com/  !

  Product idea: Statamic Cloud with DDEV local support

**Potential: Build simple SPA first, can be later run as SSR as well (if you have budget for project)**

=> **Filter Grid** -> Classic PHP Statamic, collections filters, conditions, get + VUE SFC / Svelte with Content REST API 
  - https://statamic.dev/rest-api#filtering
  - https://www.youtube.com/watch?v=sJR3pVx-M58
  - https://www.youtube.com/watch?v=mLv2DyfeELQ
  - https://dev.to/eternaldev/introduction-to-svelte-derived-store-129

=> **TODO: IMPLEMENT WITH STATAMIC AND SVELTE / VUE SFC!!**
  => Collection: Sea-Destinations 
  => https://www.youtube.com/results?search_query=vue3+pokedex 
    => https://www.youtube.com/watch?v=QJhqr7jqxVo
  => Test Deployment to Manitu, just SFTP transfer? (it's slow, but easiest way?) / Alternative: DeployNow


<hr>

- [ ] Implement Bahn zum See, have fun -> ** Statamic (free)?** 
  - **==>>> https://www.youtube.com/watch?v=XHoT8jOJa6c** 
+ Vue SFC or Svelte Comps - or - SPA via NUXT3 + Twill GraphQL? https://github.com/kallefrombosnia/twill-graphql
  - Filter Grid
  - Does it need a backend or just markdown?
- Improve my-ddev-lab docs, add screencasts for all pull actions on WP
  - get to run vite for all projects, add twill-ddev-starter

## Topics in which to grow :-)

- CMS
  - Statamic
  - Kirby
  - Bonus: Twill
  - Bonus: Strapi / Directus
    - Learn how to host via vClouds
  - Bonus: Headless WordPress + Bedrock + GraphQL
- Frontend Frameworks
  - Nuxt3
  - SvelteKit
  - (Ionic?)
- Languages / Tools
  - Vue3 Composition
  - Svelte
  - Vite
  - Tailwind
  - Laravel
  - Bonus: Typescript

EASY: SPA Frontend + Laravel/PHP Backend or SPA + Hosted Backend, SSR can be paid later as well

<hr>

- Statamic + Vue/Svelte Components ODER TWILL (TRUE OS) + Vue/Svelte => BahnZumSee Test? Twill für Hobby Projects?
  - Kirby / Statamic für prof. Agency Work?
- für größeres: Directus + Nuxt/SvelteKit?
  (headless?)


1. **Complete Realtime App** => https://codecourse.com/courses/create-a-realtime-post-timeline-with-nuxt-and-laravel

=> Repo: https://github.com/mandrasch/codecourse-laravel-nuxt-realtime (Nuxt2)


2. **Nuxt3 + Laravel** => build simple app such as grennrunners! (JWT or sanctum via DDEV / browsersync)


Develop a Multi User App, maybe with nuxt3 already?

Or use Inertia + Vue? 
or ...?

Is decoupled easier? **Nuxt - Zero config?**
Advantage nuxt: **Can be a PWA... that's cool?!** => PWAs sind scho interessant?!

or **Focus on skills like Vue, Tailwind, Typescript?**

3. Nuxt3
https://v3.nuxtjs.org/
https://github.com/epicmaxco/vuestic-ui 

https://codecourse.com/watch/getting-started-with-nuxt-3

REPO: nuxt3-test

https://blog.thepatik.com/top-5-nuxtjs-modules-for-your-next-project-2022-edition

4. Statamic + Nuxt 

https://github.com/jasonvarga/statamic-graphql-nuxt

5. Tailwind Layouting

6. Optional: Laravel Graphl + nuxt -> https://codecourse.com/courses/build-a-job-board-with-laravel-graphql-nuxt-and-apoll

(Other ways to go would be Angular or react ...)

GOAL: Full multi user app with nuxt <-> laravel

<hr>

Thoughts about SSR vs. CSR:

- Nuxt can be deployed as SPA if there is no project budget for SSR hosting
- CSR is fine for highly interactive apps without SEO https://twitter.com/devongovett/status/1528888382289494023

<hr>

Bonus: Tailwind crash course https://www.youtube.com/watch?v=dFgzHOX84xQ

<hr>


- Fullstack => Nuxt + Laravel? https://www.youtube.com/watch?v=FpwOvxsG8Js&t=32s 
  - Realtime APP => https://codecourse.com/courses/create-a-realtime-post-timeline-with-nuxt-and-laravel 
  - Laravel Graphl + nuxt -> https://codecourse.com/courses/build-a-job-board-with-laravel-graphql-nuxt-and-apollo

- At the end: TESTING? https://codecourse.com/courses/unit-testing-with-php-unit or Pest or whatever?

- Bonus: Tailwind (or another accessible frontend UI)
<hr>

- Videos: WP PULL BACKUP, DDEV PR Gitpod check, ... => put in kitdocs

- Finish kirby walkthroughs, headless WP + astro

<hr>

- BahnZumSee with WordPress, WPGraphQL, ACF, Members + Astro => bzs-api.mandrasch.eu
  - implement **paginate()** in Astro (see below)
  - => complete project!
  - https://www.youtube.com/watch?v=vTgTNVrOXZY

  => erstmal einfach Bootstrap Styles nutzen...

- Kirby KQL (-> agency context)

- Astro => Bootstrap5 => include JS via normal asset (node_modules => dist => copy it ... )




<hr>

Repo: kirby-headless-demo

- Goal: Get destinations and /destination/<slug> from kirby-headless-demo.mandrasch.eu => **FULL STATIC SITE EXPORT** 
  - **Astro - pagination - how?!** Add pagination to your blog => [Astro Crash Course #3 - API Data Fetching, Components in Markdown, Pagination, RSS, & Hosting](https://youtu.be/9wXdv7rHW2w?t=699)
  - also here: https://wpowls.co/articles/convert-wordpress-to-static-using-astro/
  - **categories/tags** - https://www.youtube.com/watch?v=m50ITGl8tPI 

=> **Bundle bahn-zum-see in monorepo for kirby (DDEV) & astro**

=> MONOREPO GITHUB ACTION
https://medium.com/@owumifestus/configuring-github-actions-in-a-multi-directory-repository-structure-c4d2b04e6312

<hr>

Watch till end:

- Kirby - Sebastian, how to get nice panels for editors? https://www.youtube.com/watch?v=QwjX8JAwBws&t=2457s
- Astro Crash Course - all parts https://www.youtube.com/watch?v=cbYr75_R15M&t=599s
- 

<hr>


- https://github.com/svelteness/kit-docs => for this repo

1. https://www.youtube.com/watch?v=QwjX8JAwBws&t=2457s complete tutorial
1. Connect SvelteKit + https://getkirby.com/plugins/getkirby/kql 

TODO: check out astro, has built-in support for svelte and aims for static sites?https://www.youtube.com/watch?v=dsTXcSeAZq8

Both SvelteKit and Astro are frameworks for building websites. SvelteKit does best with highly dynamic websites (like dashboards and inboxes) while Astro does best with highly static websites (like content and eCommerce websites).

https://github.com/withastro/docs/blob/main/src/pages/en/comparing-astro-vs-other-tools.md#sveltekit-vs-astro

=> Astro for static sites
=> SvelteKit for highly dynamic apps ... 

<hr>

Is 11ty easier for oldschool pages with kql?
https://davedavies.dev/post/how-to-use-11ty-with-headless-wordpress/

But then we can't use svelte to spice things up?

What about search? We need to connect to the server anyway? So we could sveltekit ssr maybe as well?!

=> Check out https://www.google.com/search?q=astro+headless+wordpress&oq=astro+headless+wordpress&aqs=chrome..69i57.2930j0j1&sourceid=chrome&ie=UTF-8

**TODO: WATCH**

https://www.youtube.com/watch?v=jkMvQKuDhqU

<hr>

https://remix.run/ ?
