---
title: Next.js Dev to Deployment - Brad Traversy
created: '2021-09-10T05:25:20.662Z'
modified: '2021-09-10T11:41:13.493Z'
---

# Next.js Dev to Deployment - Brad Traversy
Udemy course by Brad Traversy (https://twitter.com/traversymedia)
https://www.udemy.com/course/nextjs-dev-to-deployment

Stack: NextJS, Strapi(, Cloudinary)

Course repos:
https://github.com/bradtraversy/dj-events-frontend
https://github.com/bradtraversy/dj-events-backend

Own repo:
https://github.com/mandrasch/oerticker-frontend


## Pomodoros 🍅

- 10.09.2021 🍅🍅🍅🍅

## My notes

- extensions used: https://marketplace.visualstudio.com/items?itemName=dsznajder.es7-react-js-snippets, Prettier
- tools for debugging
  - https://chrome.google.com/webstore/detail/quick-source-viewer/cfmcghennfbpmhemnnfjhkdmnbidpanb?hl=de
    - found also https://chrome.google.com/webstore/detail/page-size-inspector/oepnndnpjiahgkljgbohnnccmokgcoln 
- proper syntax highlighting => Set file typo to javascript react (https://stackoverflow.com/a/41428535/809939)
  - https://dev.to/jastuccio/set-file-associations-per-project-in-vs-code-55n

- next/router can be used in js like this as well:

```
<button onClick={() => router.push('/')}>Test-Link mit Button</button>
```

- react icons usage, included locally as svg :+1: https://react-icons.github.io/react-icons/ 
  - library page has also a list of icons with license information :+1: https://react-icons.github.io/react-icons

- Module aliases with jsconfig https://nextjs.org/docs/advanced-features/module-path-aliases `import Button from '@/components/button'`

- Clever shorthand, only show component on startpage: ` {router.pathname === '/' && <Showcase />}`

- What i really like so far: Clean separation of components, pages/routes & styles


