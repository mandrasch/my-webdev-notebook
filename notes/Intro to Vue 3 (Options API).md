---
title: Vue Mastery / Intro to Vue 3 (Options API)
created: '2025-02-09T06:07:21.151Z'
modified: '2025-02-16T18:53:15.567Z'
---

# Vue Mastery / Intro to Vue 3 (Options API)

https://www.vuemastery.com/courses/intro-to-vue-3/intro-to-vue3

## Pomodoros 🍅

16.02.2025 🍅🍅🍅

## Notes

### Attribute binding 

- Binding: <img v-bind:src="image"> (https://vuejs.org/guide/essentials/template-syntax#attribute-bindings)

Shorthand, mostly used (!)

```html
<div :id="dynamicId"></div>
```

Same-name Shorthand:

```html
<!-- same as :id="id" -->
<div :id></div>

<!-- this also works -->
<div v-bind:id></div>
```

Multiple:

```
const objectOfAttrs = {
  id: 'container',
  class: 'wrapper',
  style: 'background-color:green'
}

<div v-bind="objectOfAttrs"></div>
```

JS Expressions:

````
<div :id="`list-${id}`"></div>
```

Function calls are also possible (https://vuejs.org/guide/essentials/template-syntax#calling-functions).

### Conditional Rendering

https://vuejs.org/guide/essentials/conditional.html

```html
<p v-if="inStock">In Stock</p>
<p v-else>Out of stock</p>
```

- `v-show` for visibility, modal etc. (display:none) - performance

Chained logic: 

```
  <p v-if="inventory > 10">In Stock</p>
            <p v-else-if="inventory <= 10 && inventory >0">Almost sold out</p>
            <p v-else>Out of stock</p>
```

### List Rendering

https://vuejs.org/guide/essentials/list.html

```
  <ul v-for="detail in details">
              <li>{{detail}}</li>
            </ul>
```

Maintain state with `key`:

```html
<template v-for="todo in todos" :key="todo.name">
  <li>{{ todo.name }}</li>
</template>
```

### Event Handling

https://vuejs.org/guide/essentials/event-handling.html

```html
  <button v-on:click="addToCart" class="button">Add to Cart</button>
```

Short hand:

```html
<button class="button" @click="addToCart">Add to Cart</button>

```

```js
const app = Vue.createApp({
    // ...
    methods: {
        addToCart() {
            this.cart = cart + 1;
        }
    }
})
```

### Class & Style Binding

https://vuejs.org/guide/essentials/class-and-style.html#class-and-style-bindings

```html
<div v-for="variant in variants" :key="variant.id":style="{backgroundColor: variant.color}" />
```

Kepab case needs to be in single quotes:

```html
<div v-for="variant in variants" :key="variant.id" :style="{'background-color': variant.color}" />
```

Binding to data object is also possible

```html
<div :style="styles" />
```

Disabled state and disabled class:

```html
<button 
  class="button" 
  :class="{ disabledButton: !inStock }" 
  :disabled="!inStock" 
  @click="addToCart">
  Add to Cart
</button>
```

### Computed Properties

https://vuejs.org/guide/essentials/computed.html

Instead of

```html
<h1>{{ brand + ' ' + product }}</h1>
```

write
```js
computed: {
  title() {
    return this.brand + ' ' + this.product
  }
}
```

Also possible:

```
data() {
  return {
    ...
    selectedVariant: 0,
    ...
  }
}, 
computed: {
  image() {
    return this.variants[this.selectedVariant].image
  }
}
```

Composition API:

```
import { reactive, computed } from 'vue'

const author = reactive({
  name: 'John Doe',
  books: [
    'Vue 2 - Advanced Guide',
    'Vue 3 - Basic Guide',
    'Vue 4 - The Mystery'
  ]
})

// a computed ref
const publishedBooksMessage = computed(() => {
  return author.books.length > 0 ? 'Yes' : 'No'
})
```

### Components & Props

https://vuejs.org/guide/components/props.html

```js
app.component('product-display', {
  template: 
    /*html*/ 
    `<div class="product-display">
      <div class="product-container">
        <div class="product-image">
          <img v-bind:src="image">
        </div>
        <div class="product-info">
          <h1>{{ title }}</h1>
  
          <p v-if="inStock">In Stock</p>
          <p v-else>Out of Stock</p>
  
          <div 
            v-for="(variant, index) in variants" 
            :key="variant.id" 
            @mouseover="updateVariant(index)" 
            class="color-circle" 
            :style="{ backgroundColor: variant.color }">
          </div>
          
          <button 
            class="button" 
            :class="{ disabledButton: !inStock }" 
            :disabled="!inStock" 
            v-on:click="addToCart">
            Add to Cart
          </button>
        </div>
      </div>
    </div>`
})
```

```html
<!-- Import Components -->
<script src="./components/ProductDisplay.js"></script>

<div id="app">
  <product-display></product-display>
</div>
```

```html
<script setup>
const props = defineProps(['foo'])

console.log(props.foo)
</script>
```

or without script setup

```js
export default {
  props: ['foo'],
  setup(props) {
    // setup() receives props as the first argument.
    console.log(props.foo)
  }
}
```

Bind property:

```html
<product-display :premium="premium"></product-display>
```

### Communicating Events

https://vuejs.org/guide/components/events.html 

- Emit events to tell parent event happened with `$emit`

```js
methods: {
  addToCart() {
    this.$emit('add-to-cart', this.variants[this.selectedVariant].id)
  }
  ...
 }
```

Adding a listener (to the component) in app scope:

```html

<product-display :premium="premium" @add-to-cart="updateCart"></product-display>
```

```js 
const app = Vue.createApp({
  data() {
    return {
      cart: [],
      ...
    }
  },
  methods: {
    updateCart() {
      this.cart += 1
    }
  }
})
```

Also works with arguments (payload):

````js
methods: {
  addToCart() {
    this.$emit('add-to-cart', this.variants[this.selectedVariant].id)
  }
  ...
 }
```

### Forms & v-model


```js
app.component('review-form', {
  template:
  /*html*/
  `<form class="review-form">
    <h3>Leave a review</h3>
    <label for="name">Name:</label>
    <input id="name" v-model="name">

    <label for="review">Review:</label>      
    <textarea id="review" v-model="review"></textarea>

    <label for="rating">Rating:</label>
    <select id="rating" v-model.number="rating">
      <option>5</option>
      <option>4</option>
      <option>3</option>
      <option>2</option>
      <option>1</option>
    </select>

    <input class="button" type="submit" value="Submit">  
  </form>`,
  data() {
    return {
      name: '',
      review: '',
      rating: null
  }
})

```


### Reactivity (Composition API)

https://vuejs.org/guide/essentials/reactivity-fundamentals#reactive

```
import { reactive } from 'vue'

const state = reactive({ count: 0 })
```

### Emit

