---
title: Vue Mastery / Real World Nuxt
created: '2025-01-16T19:46:39.335Z'
modified: '2025-02-09T17:39:14.852Z'
---

# Vue Mastery / Real World Nuxt

## Pomodoros 🍅

16.01.2025 🍅
20.01.2025 🍅
02.02.2025 🍅
07.02.2025 🍅🍅 
09.02.2025 🍅 

## Real World Nuxt 

- https://www.vuemastery.com/courses/real-world-nuxt-3/intro



## Nuxt 3 Essentials

https://www.vuemastery.com/courses/nuxt-3-essentials/nuxt-3-overview

- primary benefit: preconfigured with sensible defaults, Vue Router, Vue Meta on board

- The `<NuxtRouteAnnouncer>` component adds a hidden element with the page title to announce route changes to assistive technologies. (https://nuxt.com/docs/api/components/nuxt-route-announcer)
- Nuxt provides the <NuxtLayout> component to show layouts on pages and error pages. (https://nuxt.com/docs/api/components/nuxt-layout)
- The <NuxtPage> component is required to display pages located in the pages/ directory. (https://nuxt.com/docs/api/components/nuxt-page)

```
<template>
  <NuxtRouteAnnouncer />
  <NuxtLayout>
    <NuxtPage />
  </NuxtLayout>
</template>
```

- we will create a file called [...].js -> catchall route

### `useFetch` (not `fetch()`)

„Fetch data from an API endpoint with an SSR-friendly composable.“
https://nuxt.com/docs/api/composables/use-fetch

(!) When using `fetch` all requests will be made on Server (SSR) and on Client again. Therefore use `useFetch()` for this scenarios.

- [ ] https://www.youtube.com/watch?v=njsGVmcWviY You are using useFetch WRONG! (I hope you don't)
- useFetch --> triggered when params change => only use it top-level, use $fetch for other things instead

 
### Hydration (Rendering)

- SSR response, connecting SSR given HTML to component logic = function like classic SPA; No full page loads after initial load (client side after first request)

### Auto-imports

Nuxt automatically imports from `/components`, `/composables`, `/utils` - as well as framework provided functions such as `useFetch()``

### Composables 

> Composables in Vue 3 and Nuxt 3 are a way to create reusable, modular pieces of code that can be easily composed together to create complex functionality. They are similar to components in Vue 2, but have a few key differences that make them more powerful and easier to use. One major difference between composables and components is that composables are fully reactive, meaning that they can automatically update themselves whenever the data they depend on changes. (https://guillaumeduhan.medium.com/composables-with-nuxt-3-8631ec5dc9fb)
- [ ] composables I https://www.youtube.com/watch?v=cWX4b2qD6sg&t=30s
- [ ] composables II https://www.youtube.com/watch?v=N0QrFKBZuqA&t=0s
- [ ] https://vuejs.org/guide/reusability/composables

```
// composables/useParam.ts
export const useParam = (key: string) => {
  return useRoute().params[key].toString()
}
```

```
// posts/[page].vue
<script setup lang="ts">
const postSlug = useParam('post')
```

### defineProps()

```
const {post} = defineProps<{post: Post}>()
```

https://vuejs.org/guide/components/props.html

### ref()

````js
const isHover = ref(false)
```

```js
 <a
        class="more"
        href="#"
        @mouseenter="isHover = true"
        @mouseleave="isHover = false"
      >
```

https://vuejs.org/guide/essentials/template-refs.html#template-refs

### Routing (<NuxtLink />)

- Nuxt Routing built on top of Vue Router
- `useRoute()`

```
const postSlug = useRoute().params.post
```
```
  <NuxtLink
        class="more"
        :to="`/posts/${post.slug}`"
        @mouseenter="isHover = true"
        @mouseleave="isHover = false"
      >
        More ...
      </NuxtLink>
  ```

### Template v-if

- template can be used multiple times

```
<template>
  <main>
    <template v-if="post">
      <h1>{{ post.title }}</h1>
      <CategoryLink :category="post.category" />
      <RenderMarkdown :source="post.intro" />
```

### Layouts



### Misc

- https://vueuse.org/

