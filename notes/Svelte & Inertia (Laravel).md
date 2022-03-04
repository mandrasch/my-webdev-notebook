---
title: Svelte & Inertia (Laravel)
created: '2022-02-26T19:14:41.173Z'
modified: '2022-03-04T13:47:50.431Z'
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
- 04.03.2022 🍅🍅

## TODOs:

- [ ] ⚠️ Svelte inline css styles don't work currently?! https://laravel-mix.com/extensions/svelte & https://github.com/wewowweb/laravel-mix-svelte/
- [ ] Learn about Persistent Layouts https://inertiajs.com/pages#persistent-layouts
- [ ] What about a11y?
- [ ] Where is the difference between using the link component an `<a href="/" use:inertia>Home</a>`? (https://inertiajs.com/links#creating-links)
- [ ] Check out combination with twill? https://tech.codivores.com/ltivt-0-why-and-what
- [ ] Can we auto-reload browser with DDEV & npx mix watch?! https://laravel-mix.com/docs/6.0/livereload 
- [ ] Use npm inside of DDEV? 

## Notes

- Inertia intercepts links (https://inertiajs.com/links) if they have
  - preserve scroll position: `<Link href="/search" data={query} preserveState>Search</Link>`
