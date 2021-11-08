---
title: Next.js Dev to Deployment - Brad Traversy
created: '2021-09-10T05:25:20.662Z'
modified: '2021-11-08T20:44:24.290Z'
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
https://github.com/mandrasch/oerticker-backend


## Pomodoros 🍅

- 10.09.2021 🍅🍅🍅🍅🍅🍅🍅
- 11.09.2021 🍅🍅
- 01.10.2021 🍅🍅
- 08.10.2021 🍅🍅🍅
- 15.10.2021 🍅
- 25.10.2021 🍅🍅🍅🍅
- 29.10.2021 🍅🍅
- 30.10.2021 🍅🍅🍅🍅
- 07.11.2021 🍅🍅
- 08.11.2021 🍅🍅🍅


## My course notes

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

### Upload
```javascript
const handleSubmit = async (e) => {
        e.preventDefault()
        const formData = new FormData() // js
        formData.append('files',image)
        formData.append('ref','links')
        formData.append('refId',linkId)
        formData.append('field','image')

        const res = await fetch(`${API_URL}/upload`,{
            method:'POST',
            body: formData
        })

        if(res.ok){
            imageUploaded()
        }
    }
```

### Pagination

- https://strapi.io/documentation/developer-docs/latest/developer-resources/content-api/content-api.html#limit
- https://strapi.io/documentation/developer-docs/latest/developer-resources/content-api/content-api.html#start


```javascript
import Layout from '@/components/Layout'
import LinkItem from '@/components/LinkItem'
import {API_URL} from '@/config/index'
import Link from 'next/link'
const PER_PAGE = 2

export default function LinksPage({links, page, total}) {

    // calculate lastPage
    const lastPage = Math.ceil(total / PER_PAGE)

    return (
        <Layout title='Übersicht'>
            <h1>Links</h1>
            {links.length === 0 && <h3>Bisher noch keine Links vorhanden. :(</h3>}
            {links.map(link => (
                <LinkItem key={link.id} link={link} />
            ))}

            {page > 1 && (
                <Link href={`/links?page=${page - 1}`}>
                    <a className='btn-secondary'>Prev</a>
                </Link>
            )}
            {page < lastPage && (
                <Link href={`/links?page=${page + 1}`}>
                    <a className='btn-secondary'>Next</a>
                </Link>
            )}

        </Layout>
    )
}

export async function getServerSideProps({query:{page = 1}}){

    // calculate start page value (&_start= "Skip a specific number of entries (especially useful for pagination")
    // console.log('page requested:',page)
    const start = parseInt(page) === 1 ? 0 : ((parseInt(page) - 1) * PER_PAGE)

    // Fetch total
    const totalRes = await fetch(`${API_URL}/links/count`)
    const total = await totalRes.json()

    // Fetch links
    const linksRes = await fetch(`${API_URL}/links?_sort=date:ASC&_limit=${PER_PAGE}&_start=${start}`)
    const links = await linksRes.json()

    return{
        props:{links, page: parseInt(page),total}
    }
}
```

### Login and registration

#### Auth context

- "In a typical React application, data is passed top-down (parent to child) via props, but such usage can be cumbersome for certain types of props (e.g. locale preference, UI theme) that are required by many components within an application." https://reactjs.org/docs/context.html
- can be analyzed / debugged via react browser extension


#### HTTP-only cookies

- this cookie is set only on server side, can't be accessed via browser / via JS
- Restrict permissions in strapi backend via users permissions
- Hit api route with identifier/password => receive token

- "BUT, there is one thing that makes a stolen JWT slightly less bad than a stolen username and password: timing. Because JWTs can be configured to automatically expire after a set amount of time (a minute, an hour, a day, whatever), attackers can only use your JWT to access the service until it expires." 
- "In general, tokens should be treated like passwords and protected as such. They should never be publicly shared and should be kept in secure data stores. For browser-based applications, this means never storing your tokens in HTML5 Local Storage and instead storing tokens in server-side cookies that are not accessible to JavaScript." https://developer.okta.com/blog/2018/06/20/what-happens-if-your-jwt-is-stolen

- https://www.npmjs.com/package/cookie 

```
const data = await strapiRes.json()

        if (strapiRes.ok) {
            // Set cookie
            res.setHeader('Set-Cookie', cookie.serialize('token', data.jwt, {
                httpOnly: true,
                secure: process.env.NODE_ENV !== 'development',
                maxAge: 60 * 60 * 24 * 7, // week
                sameSite: 'strict',
                Path: '/'
            }))
            res.status(200).json({ user: data.user })
```

=> HTTPonly cookies are visible in Chrome > Cookies, but you can't acces them via document.cookie with client side javascript

https://www.youtube.com/watch?v=894seNhONF8

- helps against cross site scripting attacks (XSS), because cookie is inaccessible from javascript (third party scrips have no chance of getting this)
- although it is visible in browser cookies

### Getting links/events from user specific user (backend/strapi)

- custom strapi router

```
    {
      "method": "GET",
      "path": "/links/me",
      "handler": "links.me",
      "config": {
        "policies": []
      }
    },
```

```

module.exports = {
  // Get logged in users
  async me(ctx) {
    const user = ctx.state.user

    if (!user) {
      return ctx.badRequest(null, [{ messages: [{ id: 'No authorization header was found' }] }]);
    }

    const data = await strapi.services.links.find({
      user: user.id
    });

    if (!data) {
      return ctx.notFound();
    }

    return sanitizeEntity(data, { model: strapi.models.links });
```

- must be added in permissions
- Frontend implementation, GET-request with Beaer token:

```
    const res = await fetch(`${API_URL}/links/me`, {
        method: 'GET',
        headers: {
            Authorization: `Bearer ${token}`
        }
    })
```

### IsOwnerPolicy (backend/strapi)

- https://strapi.io/documentation/developer-docs/latest/guides/is-owner.html
- Tested with https://www.thunderclient.io/ in VSCode

### Local env(ironment)

- .env.local
- https://visgl.github.io/react-map-gl/
- https://www.npmjs.com/package/react-geocode

- https://css-tricks.com/run-useeffect-only-once/


### Deployment

#### Strapi on heroku with PostgreSQL

- https://strapi.io/documentation/developer-docs/latest/setup-deployment-guides/deployment/hosting-guides/heroku.html
- no need to install new project, but delete `yarn.lock` and gitignore `package-lock.json`
- `heroku create oerticker-backend`
- `heroku git:remote -a oerticker-backend`
- `heroku addons:create heroku-postgresql:hobby-dev --ap oerticker-backend`
- `npm i pg-connection-string pg`
  - https://www.npmjs.com/package/pg
  - https://www.npmjs.com/package/pg-connection-string 
- process.env.DATABASE_URL is automatically added to config vars of Heroku project (postgres://rilefsbXXXXXXXXXXglzxvvr:5bdd457aXXX.compute-1.amazonaws.com:5432/XXX22e2XXXXX)
- `heroku config:set NODE_ENV=production`
- set url for heroku app: `heroku config:set MY_HEROKU_URL=$(heroku info -s | grep web_url | cut -d= -f2)`

- we need to re-add the data again, because data was stored in sqlite before
- BUT: the data structure was stored in the git repo, so it is available immediately by push
- data structure changes can only be made locally as well: "For security reasons, the Content-Types Builder plugin is disabled in production. To update content structure, please make your changes locally and deploy again."

- Permissions need to be enabled again, since these were stored in local database

More on postgres:

- https://dzone.com/articles/five-key-postgres-advantages-over-mysql

<hr>

## Summary

### Likes

- It's clever to start locally with sqLite and then move it to postgres if you want to deploy, that's an easy start!
- What i really like so far: Clean separation of components, pages/routes & styles
- react-icons => sustainable way of inluding only needed icons and without extra server request
- pages/[slug].js is a very clever way of handling the route :)
- also having every change in git for strapi is cool as well + sqlite for the local dev is very easy to get started
- VScode autocomplete for imports & co works very nice as well
- `strapi.isUnauthorized()` as response is quite handy, strapi could be a nice and clean fullstack solution 


### General notes

- the separation/organization of templates is nice, but I'm currently not sure if react is maybe a little too complex in the big picture? Might try it with react-bootstrap for another project? Or look at nuxt/vue, svelte, etc.? 

### TODO in future

- responsive image sizes?!
- i18n => https://strapi.io/documentation/developer-docs/latest/development/plugins/i18n.html#usage-with-the-graphql-plugin 
- typescript usage?
- scss usage?
- bootstrap integration?
- learn about react components/build small component
- gdpr-hosting / cloudinary?
- useState() -> learn more
