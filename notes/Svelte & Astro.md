---
title: Svelte & Astro
created: '2022-04-22T09:38:57.923Z'
modified: '2022-04-23T15:14:53.718Z'
---

# Svelte & Astro

## Pomodoros 🍅

- 22.04.2022 🍅🍅🍅🍅🍅
- 23.04.2022 🍅🍅🍅🍅🍅🍅🍅🍅🍅🍅🍅🍅🍅

Astro Crash Course #1 - Layouts, Astro Components, Styles, & Pages
https://www.youtube.com/watch?v=cbYr75_R15M 

TODO: Astro Crash Course #3 - API Data Fetching, Components in Markdown, Pagination, RSS, & Hosting
https://www.youtube.com/watch?v=9wXdv7rHW2w

TODO: Building hacker news https://youtu.be/2ZEMb_H-LYE?t=3409

- **pagination - how?!** Add pagination to your blog => [Astro Crash Course #3 - API Data Fetching, Components in Markdown, Pagination, RSS, & Hosting](https://youtu.be/9wXdv7rHW2w?t=699)
  - also here: https://wpowls.co/articles/convert-wordpress-to-static-using-astro/

- **categories/tags** - https://www.youtube.com/watch?v=m50ITGl8tPI 

- **Kirby** -> disable preview in permissions for users for headless ...



## Astro

- aims for static HTML, nextjs/sveltekit for highly interactive
  - But why SSR then?
https://astro.build/blog/experimental-server-side-rendering/#motivation
- aims for smaller sites with less page weight
- aims to be faster
- js is opt-in, not default


"Yet, another framework for building sites. But this one is different. The first thing, Astro using opt-in hydration. So when you want to use javascript on your site you need to explicitly set that you are using it. It’s not like Vite, SvelteKit, or Next.js. It’s more like Eleventy with first-class support for using your client-side code."
https://marcin.page/posts/astro:-meta-framework-of-future-web-development/ 


## Astro + Kirby/KQL

Two ways of doing this: First install Kirby on webspace, use live urls. Second install DDEV Kirby locally and transfer it later (TODO: Figure out how to merge data if client edited content on live site).

1. Add api role, only access.panel=true, pages.read=true
1. Allow BasicAuth login
1. Login via POST und Basic Auth
1. Send queries via JSON

https://github.com/getkirby/kql#sending-post-requests

- Kirby 

> The Kirby QL API takes POST requests with standard JSON objects and returns highly customized results that fit your application.

Repo: 

Biggest advantage of Kirby: Doesn't need a database, therefore it is easier maintainable via GIT?

Svelte - Filtering ... 
https://www.youtube.com/watch?v=aZZ6Cko4nKU&t=1543s


## Astro + WordPress as example

[A crash course in Jamstack with Headless WP, Astro, and Buddy | Buddy Webinar #9](https://www.youtube.com/watch?v=jkMvQKuDhqU)

- resulting site of website is smaller

https://wpowls.co/articles/convert-wordpress-to-static-using-astro/

## Astro + Bootstrap

Sveltestrap isn't working, got stuck there ... https://github.com/bestguy/sveltestrap/issues/463

Check out https://framework7.io/ - has svelte support? Also for sveltekit?!

https://github.com/AgnosticUI/agnosticui/tree/master/agnostic-astro in the works... 


https://www.youtube.com/watch?v=z15YLsLMtu4&list=PLz8Iz-Fnk_eTpvd49Sa77NiF8Uqq5Iykx&t=2917s


TODO: https://stackblitz.com/github/withastro/astro/tree/latest/examples/with-vite-plugin-pwa?on=stackblitz Vite-Plugin-PWA Demo ...

TODO: dynamic routes, https://discord.com/channels/830184174198718474/845451724738265138/896787058641731634

=> Main advantage of astro over 11ty => we can sprinkle svelte in it?!

TODO: nuxt ?


## Storyblok + Astro?

https://www.storyblok.com/tp/add-a-headless-cms-to-astro-in-5-minutes 

## More 

https://github.com/one-aalam/awesome-astro


## Cockpit
https://getcockpit.com/ -> it's api first?
