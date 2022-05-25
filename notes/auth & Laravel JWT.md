---
title: 'Nuxt, nuxt/auth & Laravel JWT'
created: '2022-05-06T10:52:01.714Z'
modified: '2022-05-25T21:18:48.180Z'
---

# Nuxt, nuxt/auth & Laravel JWT

- Course: [create-a-realtime-post-timeline-with-nuxt-and-laravel](https://codecourse.com/watch/create-a-realtime-post-timeline-with-nuxt-and-laravel)
  - _we replaced sanctum with PHP-Open-Source-Saver/jwt-auth, because sanctum required same top-level-domain which was complicated for a local setup with different domains_
- Uses
  - Laravel with Fortify and https://github.com/PHP-Open-Source-Saver/jwt-auth
  - Nuxt 2 with nuxt/auth and https://auth.nuxtjs.org/providers/laravel-jwt/

## Pomodoros 🍅

- 06.05.2022 🍅🍅🍅🍅🍅🍅🍅🍅
- 24.05.2022 🍅🍅🍅🍅🍅🍅🍅🍅🍅
- 25.05.2022 🍅🍅🍅 + 0,5

## Next

- Login with real form ... (Vue) instead of hard coded
- Access user restricted route 
- **Continue https://codecourse.com/watch/create-a-realtime-post-timeline-with-nuxt-and-laravel?part=authenticating-liker-project-nuxt**

## Notes

- Advantages Nuxt
  - options for js/ts, UI (vuetify,bootstrap vue, etc.), SSR or SPA, etc. while install available

## Course: Create a Realtime Post Timeline with Nuxt and Laravel


  - https://laravel.com/docs/9.x/fortify - Usually used with blade templates, but can be used headless as well
  - https://laravel.com/docs/9.x/sanctum _Laravel Sanctum provides a featherweight authentication system for SPAs (single page applications), mobile applications, and simple, token based APIs._
    - supports API tokens as well as SPA mode (we use SPA mode)
  - https://auth.nuxtjs.org/ 
    - There is a provider for Laravel Sanctum! Nice! :-o https://auth.nuxtjs.org/providers/laravel-sanctum

- Check routes `ddev artisan route:list` (--compact not working)
- Add a user via tinker: `ddev artisan tinker` and 

```
User::factory()->create(['name'=>'Matthias', 'email'=>'matthias@example.com', 'password'=>bcrypt('ilovecats')])
```

- ⚠️ Laravel Sanctum only works on same top level domain, not between localhost and .ddev.site
- **Therefore we use https://github.com/PHP-Open-Source-Saver/jwt-auth, see: https://blog.logrocket.com/implementing-jwt-authentication-laravel-9/#install-and-set-up-jwt**

- Plugins used:
  - https://www.npmjs.com/package/vue-observe-visibility

## Other relevant courses:

- Laravel Graphl + nuxt -> https://codecourse.com/courses/build-a-job-board-with-laravel-graphql-nuxt-and-apoll
- Laravel Basics https://codecourse.com/courses/laravel-basics


