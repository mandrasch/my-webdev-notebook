---
title: Svelte & Svelte-Kit
created: '2021-10-15T13:58:50.298Z'
modified: '2021-12-04T13:50:21.988Z'
---

# Svelte & Svelte-Kit

## Pomodoros 🍅

- 15.10.2021 🍅
- 16.10.2021 🍅🍅🍅🍅
- 12.11.2021 🍅🍅
- 03.12.2021 🍅🍅🍅🍅🍅🍅🍅🍅🍅🍅🍅
- 04.12.2021 🍅🍅🍅🍅

## General

- Svelte adds *reactivity* to components/elements, therefore it is easier to implement interactive elements (in comparison to vanilljs, jquery)
- Svelte tries to avoid *boilerplatey* code repetition
- Svelte is a compiler which produces vanilla js
- Svelte uses scoped css
- SvelteKit is a framework for building web applications

## Building tzettel (little prototype)

- Svelte strap https://sveltestrap.js.org/?path=/story/components--get-started
 "How to use SASS in Sveltekit? - Sveltekit Tutorial - 15" https://www.youtube.com/watch?v=yN8R9pKqtV8
- https://github.com/sveltejs/svelte-preprocess
  - Install: https://github.com/sveltejs/svelte-preprocess/blob/main/docs/getting-started.md
- https://github.com/sveltejs/kit/tree/master/packages/adapter-static#github-pages
- relative links https://javascript.plainenglish.io/sveltekit-github-pages-4fe2844773de

## SvelteKit crash course

https://www.youtube.com/watch?v=UU7MgYIbtAk

CURRENT PROGRESS: https://youtu.be/UU7MgYIbtAk?t=1787
https://www.youtube.com/watch?v=UU7MgYIbtAk&t=533s

- Prettier => make sure to set the svelte vscode extensions formatter, because it has the svelte prettier plugin integrated. Example for `.vscode/settings.json`: 

```
{
	"editor.formatOnSave": true,
  "editor.defaultFormatter": "esbenp.prettier-vscode",
	"[svelte]": {
		"editor.defaultFormatter": "svelte.svelte-vscode"
	}
}
```

- `<Link>`not needed as in nextjs, just use anchor tags

- Create a new store (https://svelte.dev/docs#writable)

```javascript
const count = writable(0);

export const pokemon = writable([])

// log it out with data sign (its reactive)
console.log('pokemons', $pokemons);
```

- `npm install -D tailwindcss autoprefixer`
- https://tailwindcss.com/docs/just-in-time-mode JIT


#### TODO:

- What about `pathPrefix (11ty)`, deploy to subdirectory?

### Offical website tutorial

https://svelte.dev/tutorial/basics

- "Svelte converts your app into ideal JavaScript at build time, rather than interpreting your application code at run time. " 
- Scoped CSS => styles don't leak in https://svelte.dev/tutorial/nested-components
- reactive declarations - "re-run this code whenever any of the referenced values change", `$: doubled = count * 2;` (https://svelte.dev/tutorial/reactive-declarations)
  - these also can run functions, e.g. console.log `$: console.log(`the count is ${count}`);`

  ```javascript
  $: {
	  console.log(`the count is ${count}`);
	  alert(`I SAID THE COUNT IS ${count}`);
  }
  ```
  - even in front of if-blocks:

  ```javascript
  $: if (count >= 10) {
	alert(`count is dangerously high!`);
	count = 9;
  }
  ```

- simple `array.push` does not trigger update automatically
```javascript
numbers.push(numbers.length + 1);
numbers = numbers; // this needs to be done
// or rewrite as
numbers = [...numbers, numbers.length + 1];
```
  - "A simple rule of thumb: the name of the updated variable must appear on the left hand side of the assignment." (https://svelte.dev/tutorial/updating-arrays-and-objects)

- each => define key `{#each things as thing (thing.id)}`

- Events: modifiers such as `once`, `preventDefault` are available and can be chained:

```javascript
<button on:click|once|preventDefault={handleClick}>
	Click me
</button>
```

- Components can dispatch events, which can be then handled by the parent file (where the component is imported & included) https://svelte.dev/tutorial/component-events
  - deeply nested components, shorthand for forwarding messages `<Inner on:message/>` (they won't bubble up normally)
    - Inner => `dispatch('message', {text: 'Hello!'});`
    - Outer => `<Inner on:message/>` (shorthand for forwarding all)
    - App.svelte => `<Outer on:message={handleMessage}/>`
  - this is usable for normal HTML elements as well `<button on:click>`

**Forms / inputs**

- two-way-data-binding `<input bind:value={name}>`, https://svelte.dev/tutorial/text-inputs
  - svelte takes care automatically regarding int, bool, etc.
    - numeric: `<input type=number bind:value={a} min=0 max=10>` (int)
    - checkbox: `<input type=checkbox bind:checked={yes}>` (boolean)
    - radio: `<input type=radio bind:group={scoops} name="scoops" value={1}>`https://svelte.dev/tutorial/group-inputs
    - textarea: `<textarea bind:value={value}></textarea>`
    - `<select bind:value={selected}>`
  - binding inside `#each` is possible! https://svelte.dev/tutorial/each-block-bindings

**bind:this=**

- `bind:this={field}` https://svelte.dev/tutorial/component-this

**Lifecycle**

- `onMount` https://svelte.dev/tutorial/onmount
  - "It's recommended to put the fetch in onMount rather than at the top level of the <script> because of server-side rendering (SSR). With the exception of onDestroy, lifecycle functions don't run during SSR, which means we can avoid fetching data that should be loaded lazily once the component has been mounted in the DOM." (TODO: What is meant by this exactly? Lazily loaded is better?)
- `onDestroy`, e.g. for intervals (https://svelte.dev/tutorial/ondestroy)
- `beforeUpdate` and `afterUpdate` (https://svelte.dev/tutorial/update)
- `tick` https://svelte.dev/tutorial/tick

**Stores**

- has set, update, subscribe and unsubscribe (https://svelte.dev/tutorial/writable-stores)

```javascript
// stores.js
import { writable } from 'svelte/store';
export const count = writable(0);

// usage:
import { count } from './stores.js';

let count_value;

count.subscribe(value => {
	count_value = value;
});
```

- Autosubscription: https://svelte.dev/tutorial/auto-subscriptions
  - `<h1>The count is {$count}</h1>` or in script just as `$`
- readable stores https://svelte.dev/tutorial/readable-stores
- derived stores https://svelte.dev/tutorial/derived-stores
- custom stores (TODO: What does writeable(0)?) https://svelte.dev/tutorial/custom-stores

- store bindings (https://svelte.dev/tutorial/store-bindings)
  - "The $name += '!' assignment is equivalent to name.set($name + '!')."

**Motion / Animating value changes**

- `tweened` (https://svelte.dev/tutorial/tweened) and `spring` (https://svelte.dev/tutorial/spring)

**Transitions**


Wow, deferred: https://svelte.dev/tutorial/deferred-transitions (TODO example) => crossfade()

full example: https://svelte.dev/tutorial/animate

** Actions **

- third party include https://svelte.dev/tutorial/actions 

** Classes **

Shorthand in svelte, `class:selected=`

```javascript
<button
	class:selected="{current === 'foo'}"
	on:click="{() => current = 'foo'}"
>foo</button>
```
"The .selected class is added to the element whenever the value of the expression is truthy, and removed when it's falsy."

Also: https://svelte.dev/tutorial/class-shorthand

** Component childs: Slot **

```javascript
<div class="box">
	<slot>
		<em>no content was provided</em>
	</slot>
</div>
```

Advanced usage via slot="" (named slots, https://svelte.dev/tutorial/named-slot)

```javascript
<ContactCard>
	<span slot="name">
		P. Sherman
	</span>
```

```javascript
<article class="contact-card">
	<h2>
		<slot name="name">
			<span class="missing">Unknown name</span>
		</slot>
	</h2>
```
More information: https://svelte.dev/tutorial/optional-slots

### Svelte crash course - Traversymedia (not fully watched yet)

https://www.youtube.com/watch?v=3TVy6GdtNuQ
  
  - easier to use, state management easier (although no big project coded)?
  - addition to SvelteKit (same as nextjs)

### TODO


- https://svelte.dev/tutorial/optional-slots
- https://svelte.dev/tutorial/slot-props
- https://strapi.io/blog/how-to-create-a-blog-with-svelte-kit-strapi
