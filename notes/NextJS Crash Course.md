---
tags: [nextjs]
title: NextJS Crash Course
created: '2021-08-27T13:28:11.408Z'
modified: '2021-08-27T17:41:44.594Z'
---

# NextJS Crash Course

[Next.js Crash Course 2021 - Traversy Media (YouTube)](https://www.youtube.com/watch?v=mTz0GXj8NN0)
 
## Pomodoros 🍅

27.08.2021 🍅🍅🍅🍅🍅

## Notes

- NextJs allows rendering server-side as well

```
npx create-next-app next-crash-course --use-npm
code . #open in vscode
```

Module (component) styles can be imported via naming convention xyz.module.css:

`import myStylesName from '../styles/Home.module.css` 

Add content for `<head>` via

```
import Head from 'next/head'
export default function Home() {
  return (
    <div>
      <Head>
        <title>WebDev News</title>
        <meta name="keywords" content="web development, programming" />
      </Head>
      <h1>Welcome to Next</h1>
    </div>
  )
}
```

`_app.js` wraps around the page content, therefore here are global styles placed here

`import '../styles/globals.css'`

Naming convention is lowercase for pages, uppercase for components.

## Component level CSS

<blockquote>CSS Modules locally scope CSS by automatically creating a unique class name. This allows you to use the same CSS class name in different files without worrying about collisions.</blockquote>

Source: [NextJS Docs](https://nextjs.org/docs/basic-features/built-in-css-support#adding-component-level-css)

```
<button
      type="button"
      // Note how the "error" class is accessed as a property on the imported
      // `styles` object.
      className={styles.error}
    >
```
This will automatically be transformed to a class with unique name such as `class="error_ch37j"`.

Add a navigation:

```
import Nav from './Nav'
import styles from '../styles/Layout.module.css'

const Layout = ({ children }) => {
    return (
        <>
        <Nav />
        <div className={styles.container}>
            <main className={styles.main}>
                {children}
            </main>
        </div>
        </>
    )
}

export default Layout
```

## Styled JSX

https://nextjs.org/blog/styling-next-with-styled-jsx

```
const Header = () => {
    const x = 2
    return (
        <div>
            <h1 className='title'>
                <span>WebDev</span> News
            </h1>
            <style jsx>
                {`
                .title{
                    color:${x > 3 ? 'red' : 'blue'};
                }
            `}
            </style>
        </div>
    )
}
```

## Custom document (server-rendered)

- add html-lang attribute for example, or body class tags
- BUT: meta tags can be added in <Head>, no need for custom document

https://nextjs.org/docs/advanced-features/custom-document 

## Data fetching 

- three methods: 
  - "getStaticProps (Static Generation): Fetch data at build time."
  - "getStaticPaths (Static Generation): Specify dynamic routes to pre-render pages based on data."
  - "getServerSideProps (Server-side Rendering): Fetch data on each request."
- we use `getStaticProps`
- "fake" json rest api for testing: https://jsonplaceholder.typicode.com/

- apply props to components, which were fetched:
```
<ArticleList articles={articles} />

...

export const getStaticProps = async () => {
  const res = await fetch('https://jsonplaceholder.typicode.com/posts?_limit=6')
  const articles = await res.json()
  // console.log('received articles',articles)
  return {
    props: {
      articles
    }
  }
}
```

## Nested routes

**Get variables via router (just as example)**

Create `pages/article/[id]/`-folder, create index.js and use next router to get variables:

```
// single article page

import {useRouter} from 'next/router'

const article = () => {
    const router = useRouter()
    const {id} = router.query;

    return (
        <div>
            This is article with id {id}
        </div>
    )
}

export default article
```

**Get data variables via nextjs / api **

"getServerSideProps (Server-side Rendering): Fetch data on each request."


```
// single article page /w data fetching

import Link from "next/link"

const article = ({ article }) => {
    return (
        <>
            <h1>{article.title}</h1>
            <p>{article.body}</p>
            <br/ >
            <Link href="/">Go Back</Link>
        </>
    )
}


export const getServerSideProps = async (context) => {
    const res = await fetch(`https://jsonplaceholder.typicode.com/posts/${context.params.id}`)
    const article = await res.json()

    return {
        props: {
            article
        }
    }
}

export default article


```

**Combination for static data fetching**

This is faster, combination of 
- "getStaticProps (Static Generation): Fetch data at build time."
- "getStaticPaths (Static Generation): Specify dynamic routes to pre-render pages based on data."

"If a page has dynamic routes (documentation) and uses getStaticProps it needs to define a list of paths that have to be rendered to HTML at build time.". In our case:

```
paths [
  { params: { id: '1' } },
  { params: { id: '2' } },
  { params: { id: '3' } },
  { params: { id: '4' } },
  { params: { id: '5' } },
  ...
```

Therefore this is achieved with 

```
export const getStaticPaths = async () => {
    const res = await fetch(`https://jsonplaceholder.typicode.com/posts`)
    const articles = await res.json()
    const ids = articles.map((article) => article.id)
    const paths = ids.map((id)=>({params:{id:id.toString()}}))
    console.log('paths',paths)
    /* because we need this:
     * paths:{
     *       params:{id:'1', id: '2'}
     *  }
     */
    return{
        paths,
        fallback:false
    }
}
```

## Export a static website

https://nextjs.org/docs/advanced-features/static-html-export

Change package.json, run `npm run build`

```
"build": "next build && next export",
```

This will export the page to the `out`-folder. 

Serve it with `npx serve -s out/ -p 8000`.

(https://www.npmjs.com/package/serve)

**Error because of next/image**

https://nextjs.org/docs/messages/export-image-api

Ran into this because standard next js project imports next/image. Removed it by now.

<hr>

Continue at https://youtu.be/mTz0GXj8NN0?t=3140

## VSCode helper

- `rafce`(react arrow function export component) - [VS Code ES7 React/Redux/React-Native/JS snippets](https://marketplace.visualstudio.com/items?itemName=dsznajder.es7-react-js-snippets)
- Just type <Link and enter, vs code will automatically add `import Link from 'next/link'


## Credits

Some text contents are quoted from https://nextjs.org/docs/, MIT license
