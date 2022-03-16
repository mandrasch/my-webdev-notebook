---
title: Svelte & Inertia (Laravel)
created: '2022-02-26T19:14:41.173Z'
modified: '2022-03-16T15:35:45.924Z'
---

# Svelte & Inertia (Laravel)

- [x] [Laracast series: Build Modern Laravel Apps Using Inertia.js](https://laracasts.com/series/build-modern-laravel-apps-using-inertia-js) 🥳
- [ ] [Laracast series: Inertia and SPA Techniques](https://laracasts.com/series/inertia-and-spa-techniques)

- Repo: 

## Pomodoros 🍅

- 26.02.2022 🍅🍅🍅
- 03.03.2022 🍅🍅
- 04.03.2022 🍅🍅🍅🍅
- 11.03.2022 🍅🍅🍅🍅🍅🍅🍅🍅
- 12.03.2022 🍅
- 13.03.2022 🍅🍅
- 16.03.2022 🍅🍅+0,5

## Next tasks

- [ ] Start demo app greenrunners => "add a run", "edit a run", "register", "mark as paid
- [ ] Variable layout not working, see inertia discord

## TODOs:

- [ ] ⚠️ Svelte inline css styles don't work currently?! https://laravel-mix.com/extensions/svelte & https://github.com/wewowweb/laravel-mix-svelte/
- [ ] What about a11y?
- [ ] Check out combination with twill? https://tech.codivores.com/ltivt-0-why-and-what
- [ ] Can we auto-reload browser with DDEV & npx mix watch?! https://laravel-mix.com/docs/6.0/livereload  => doesnt work?! https://laracasts.com/discuss/channels/elixir/how-to-use-livereload?page=1&replyId=717892
  - Use browsersync instead? https://www.youtube.com/watch?v=sVrClrWwOwU
- [ ] Use npm inside of DDEV? 
- [ ] https://render.com/blog/svelte-design-patterns
- [ ] Default Layouts do not work with svelte? Create demo and ask in inertia svelte discord https://laracasts.com/series/build-modern-laravel-apps-using-inertia-js/episodes/13 
    - Used for code splitting as well ... https://laracasts.com/series/build-modern-laravel-apps-using-inertia-js/episodes/14 
- [ ] Svelte Ping CRM Gitpod 
    - check default layouts ...

## Notes

- Inertia intercepts links (https://inertiajs.com/links) if they have `use:inertia` or via `<Link>`-component (https://inertiajs.com/links)
  - preserve scroll position: `<Link href="/search" data={query} preserveState>Search</Link>`
- [Persistent layouts](https://inertiajs.com/pages#persistent-layouts)

### Throtteling vs debounce (lodash)

- Search field input event -> would create a lot of requests, change only triggered when user leaves field
  - throttle: execute action once every X milliseconds
  - debounce: merge multiple actions
  - difference: https://stackoverflow.com/questions/25991367/difference-between-throttling-and-debouncing-a-function#:~:text=Throttling%20will%20delay%20executing%20a,event%20that%20fires%20multiple%20times.
  - https://css-tricks.com/the-difference-between-throttling-and-debouncing/
  - depends on use case 
  - See https://stackoverflow.com/a/46106932/809939
  - debounce => nicer for server load

  ### Auth quickstart

  - https://laravel.com/docs/8.x/authentication#authenticating-users
  - `ddev artisan make:policy UserPolicy --model=User``
    - 
