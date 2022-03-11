---
title: Svelte & Inertia (Laravel)
created: '2022-02-26T19:14:41.173Z'
modified: '2022-03-11T17:01:29.147Z'
---

# Svelte & Inertia (Laravel)

- https://laracasts.com/series/build-modern-laravel-apps-using-inertia-js/episodes/1
- and https://dev.to/dansvel/laravel-and-svelte-with-inertia-5fl

- Repo: 

- Continue here: https://laracasts.com/series/build-modern-laravel-apps-using-inertia-js/episodes/4

- Introduction: https://www.youtube.com/watch?v=rg-eZBw50KI&list=WL&index=1&t=1486s

## Pomodoros 🍅

- 26.02.2022 🍅🍅🍅
- 03.03.2022 🍅🍅
- 04.03.2022 🍅🍅🍅🍅
- 11.03.2022 🍅🍅🍅🍅🍅🍅🍅

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
  - 
