---
title: Next.js Dev to Deployment - Brad Traversy
created: '2021-09-10T05:25:20.662Z'
modified: '2021-10-08T17:19:51.423Z'
---

# Next.js Dev to Deployment - Brad Traversy
Udemy course by Brad Traversy (https://twitter.com/traversymedia)

Course: https://www.udemy.com/course/nextjs-dev-to-deployment
Free video: https://www.youtube.com/watch?v=mTz0GXj8NN0

Stack: NextJS, Strapi(, Cloudinary)

Course repos:
https://github.com/bradtraversy/dj-events-frontend
https://github.com/bradtraversy/dj-events-backend

Own repo:
https://github.com/mandrasch/oerticker-frontend


## Pomodoros 🍅

- 10.09.2021 🍅🍅🍅🍅🍅🍅🍅
- 11.09.2021 🍅🍅
- 01.10.2021 🍅🍅
- 08.10.2021 🍅🍅🍅

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

- API routes can't be used with `next export`

- getStaticProps => built at build time, revalidate every second

```
export async function getStaticProps(){
...
 return{
        props:{events},
        revalidate: 1
    }
}
```

- get URL params for urls like /events/SLUG/:

  "query: Object - The query string parsed to an object. It will be an empty object during prerendering if the page doesn't have data fetching requirements. Defaults to {}" (https://nextjs.org/docs/api-reference/next/router#router-object) 

```
export async function getServerSideProps({query:{slug}}){
    console.log('slug: '+slug);
```

- next/image supports `object-fit:cover` (https://nextjs.org/docs/api-reference/next/image#objectfit):

```
 <Image src={link.image ? link.image : '/images/eichkatzerl_cc0_own_photo.png'} layout='fill' objectFit='cover' objectPosition='center center' alt='' />
```

- Search / Query Filter: _contains

https://strapi.io/documentation/developer-docs/latest/developer-resources/content-api/content-api.html#filters

```
https://STRAPI_URL:1337/?entity/name_contains=searchinput
```

Multiple search queries combined: 

https://strapi.io/documentation/developer-docs/latest/developer-resources/content-api/content-api.html#filters

```
const query = qs.stringify({
  _where: [{ stars: 1 }, { pricing_lte: 20 }],
});

await request(`/restaurants?${query}`);
// GET /restaurants?_where[0][stars]=1&_where[1][pricing_lte]=20
```
* qs = https://www.npmjs.com/package/qs

! Search page needs to use `getServerSideProps` instead of getStaticProps

### Likes

- What i really like so far: Clean separation of components, pages/routes & styles
- react-icons => sustainable way of inluding only needed icons and without extra server request

### Strapi backend

- SQLite is used on dev, PostgreSQL on production
- Quickstart project, selected no for template question
- Switched to node 14.x with `sudo n`
- Peacock for different colors on vscode windows
- `npm run develop`
- https://www.npmjs.com/package/strapi-provider-upload-cloudinary?activeTab=readme

### Form handling / state

- https://reactjs.org/docs/hooks-state.html

### Strapi - automatic slug creation
```
npm i slugify
```

https://strapi.io/documentation/developer-docs/latest/guides/slug.html#auto-create-update-the-slug-attribute

### Modal components

https://devrecipes.net/modal-component-with-next-js/

- use of custom _document.js

### TODO in future

- responsive image sizes?!
- i18n => https://strapi.io/documentation/developer-docs/latest/development/plugins/i18n.html#usage-with-the-graphql-plugin 
- typescript usage?
- scss usage?
- bootstrap integration?
- learn about react components/build small component
