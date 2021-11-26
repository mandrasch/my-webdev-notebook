---
title: Svelte & (headless) WordPress
created: '2021-11-26T19:30:56.384Z'
modified: '2021-11-26T20:58:49.634Z'
---

# Svelte & (headless) WordPress

1. https://www.youtube.com/watch?v=94FZvB6B_c0


## Pomodoros 🍅

- 26.11.2021 🍅🍅🍅

## Notes

- https://www.wpgraphql.com/

- for production, a library such as svelte-query (https://github.com/SvelteStack/svelte-query), apollo-client (https://www.apollographql.com/docs/react/), urql (https://formidable.com/open-source/urql/) should be used instead of fetch

- get post by slug via query variables

```
	const query = `
      query getPostBySlug($slug: ID!) {
        post(id: $slug, idType: SLUG) {
   
   // ...

   const response = await fetch(import.meta.env.VITE_PUBLIC_WORDPRESS_API_URL, {
			method: 'POST',
			headers: {
				'Content-Type': 'application/json'
			},
			body: JSON.stringify({
				query,
				variables: {
					slug: page.params.slug
				}
			})
		});

```

### Gutenberg

"we learned that WordPress does not currently provide a complete server-side registry of Gutenberg blocks, and that as a result, there are two primary, viable options for rendering blocks in headless WordPress projects:

- Render Gutenberg Blocks as HTML
- Use WPGraphQL Gutenberg" 

(https://developers.wpengine.com/blog/gutenberg-in-headless-wordpress-wpgraphql-gutenberg)

## TODOs

WATCH ALONG HERE: Gutenberg in Headless WordPress: Render Blocks as HTML https://youtu.be/Naz0Fv_VVQk?t=423 

- [ ] Fix internal links
- [ ] Convert anchor tags

- [ ] Check out Gutenberg in Headless WordPress: WPGraphQL Gutenberg as well https://www.youtube.com/watch?v=4Ybro_joKMk

_**TODO: Read https://www.wpgraphql.com/2021/03/09/gutenberg-and-decoupled-applications/ **_



- understand https://svelte.dev/tutorial/module-exports
- what about pathPrefix, as seen in 11ty?
- images from another server/domain => issue for CORS?
- What about gutenberg layouts? how does that work?
- idea: use DDEV inside the repo, add WPCLI commands for graphiql => demonstrate a single repo way of running this?
  - where could the data schema be stored? in a json file for ACF or something else?

