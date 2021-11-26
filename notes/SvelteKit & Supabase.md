---
title: SvelteKit & Supabase
created: '2021-11-26T12:35:29.411Z'
modified: '2021-11-26T19:32:20.141Z'
---

# SvelteKit & Supabase

1. https://www.youtube.com/watch?v=j4AV2Liojk0 
1. https://www.youtube.com/watch?v=toP1jjRpYQs
1. https://www.youtube.com/watch?v=xWaJZcFs72c
1. TODO:https://www.youtube.com/watch?v=7_9rUtwM-q0

TODO: https://supabase.com/docs/guides/with-svelte

## Pomodoros 🍅

- 26.11.2021 🍅🍅🍅🍅🍅🍅

## General Notes

- extremly fast setup
- realtime subscription seems to be very easy
- Postgres Row Level Security seems to be easy as well, as least for simple tasks
  - but for realtime updates, only public data should be used currently because RLS is not available (https://supabase.com/docs/going-into-prod)

- How does it compare to strapi, headless wordpress, directurs etc.? Is it sustainable?
  - strapi can be used locally with sqlite, but how do you maintain it afterwards? heroku => connect a remote db, how do you test it locally?
  - DDEV + wordpress + sveltekit could be a solution for low-budget hosting?
  - how hard / cpu consuming is supabase selfhosting? https://www.youtube.com/watch?v=HCqta43JHkU
  - how can multiple environments be organized in supabase? https://github.com/supabase/supabase/discussions/542


Other notes:
- Load testing as SaaS https://k6.io/cloud
