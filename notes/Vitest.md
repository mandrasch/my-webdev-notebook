---
title: Vue Mastery / Vitest
created: '2025-02-09T06:07:53.722Z'
modified: '2025-02-09T14:43:59.504Z'
---

# Vue Mastery / Vitest

- https://www.vuemastery.com/courses/quick-tests-with-vitest/testing-a-page-e2e-testing/
- https://vitest.dev/

## Pomodoros 🍅

09.02.2025 🍅🍅🍅🍅

- Unit vs. Integration vs. E2E test

## Notes

- `npm run test:unit`
- Assertions of `expect` https://vitest.dev/api/expect

```js
// src/components/__tests__/squareroot.test.js
import { describe, it, expect } from "vitest"

describe("square root", () => {
  it("finds square root", () => {
    expect(Math.sqrt(49)).toBe(7);
  })
})
```
### Test components

- mount compontents in tests via vue-utils stub (https://test-utils.vuejs.org/guide/advanced/stubs-shallow-mount)

```bash
npm i  --dev @vue/
test-utils `
```

- happy dom and jsdom --> package.json, jsdom installed automatically (via `environment` in `vitest.config.js`)

```js
// src/components/___tests___/NotificationToast.vue
import { mount } from "@vue/test-utils";
import NotificationToast from "../NotificationToast.vue";
import { describe, expect, test } from "vitest";

describe("Notification Component", () => {
  test("renders the correct style for error", () => {
    const status = "error"

    // our stub component
    const wrapper = mount(NotificationToast, {
      props: { status }
    })

    // https://vitest.dev/api/expect#expect-arraycontaining
    expect(wrapper.classes()).toEqual(expect.arrayContaining(['notification--error']))
  })

   test('notification slides up when message is empty', () => {
    const message = ''
    const wrapper = mount(NotificationToast, {
      props: { message }
    })
    expect(wrapper.classes("notification--slide")).toBe(false)
  })

  test('emits event when close btn clicked', async () => {
    const wrapper = mount(NotificationToast, {
      data() {
        return {
          clicked: false
        }
      }
    })
    const closeButton = wrapper.find('button')
    await closeButton.trigger('click')
    // check event
    expect(wrapper.emitted()).toHaveProperty('clear-notification')
  })


  test("renders correct message to viewer", () => {
    const message = "Something happened, try again";
    const wrapper = mount(NotificationToast, {
      props: { message },
    });
    expect(wrapper.find("p").text()).toBe(message);
  });
```

### Snapshot testing

- `expect(wrapper.html()).toMatchSnapshot()`
- stored in `__tests/snapshots/*.test.js.snap`:

```
// Vitest Snapshot v1, https://vitest.dev/guide/snapshot.html

exports[`Notification Component > renders the correct style for error 1`] = `
"<div role="alert" class="notification notification--error">
  <p class="notification__text"></p><button title="close" class="notification__button"> ✕ </button>
</div>"
`;
```

- when it fails, you can use `press up to update snapshot` 

Inline snapshots:

```
 test("renders the correct style for error", () => {
    const type = "error";
    const wrapper = mount(notification, {
      props: { status },
    });
    expect(wrapper.html()).toMatchInlineSnapshot(
      `"<div role=\\\\"alert\\\\" class=\\\\"notification notification--error\\\\"><p class=\\\\"notification__text\\\\"></p><button title=\\\\"close\\\\" class=\\\\"notification__button\\\\"> ✕ </button></div>"`
    );
  });
```

### API Calls (Mocking)

- `vi.spyOn` intercepts calls via .mockResolvedValueOnce (https://vitest.dev/api/mock#mockresolvedvalueonce):

```
vi.spyOn(axios, 'post').mockResolvedValueOnce({ data: mockPost })
```

```
import axios from 'axios'
import PostCard from '../PostCard.vue'
import { mount, flushPromises } from '@vue/test-utils'

const mockPost = {
  userId: 1,
  id: 1,
  title: 'sunt aut facere repellat provident occaecati excepturi optio reprehenderit',
  body: 'quia et suscipit\nsuscipit recusandae consequuntur expedita et cum\nreprehenderit molestiae ut ut quas totam\nnostrum rerum est autem sunt rem eveniet architecto'
}

describe('Post Card Component', () => {
  test('can fetch and display a post', async () => {
    vi.spyOn(axios, 'get').mockResolvedValueOnce({ data: mockPost })

    const wrapper = mount(PostCard)

    expect(wrapper.html()).toContain('Loading...')

    await flushPromises()

    // new
    expect(wrapper.find('[data-testid="post-title"]').text()).toBe(mockPost.title)

    expect(wrapper.find('[data-testid="post-body"]').text()).toBe(mockPost.body)
  })

  test('can display an error message if fetching a post fails', async () => {
    vi.spyOn(axios, 'get').mockRejectedValueOnce(new Error('Error occurred'))

    const wrapper = mount(PostCard)

    expect(wrapper.html()).toContain('Loading...')

    await flushPromises()

    expect(wrapper.find('[data-testid="error-message"]').text()).toBe('Error occurred')
  })
})
```



### Enabled globals

> Let’s configure it globally. This way, we can use functions (such as describe, expect and test) from Vitest without having to import them every single time.

```
export default mergeConfig(
  viteConfig,
  defineConfig({
    test: {
      globals: true,

```

### E2E Testing

- [ ] does not work with latest vitest

```
describe('Posts App', () => {
  test('user can create a new post', async () => {
    vi.spyOn(axios, 'post').mockResolvedValueOnce({ data: mockPost })

    const wrapper = mount(App)

    //fill in the input fields
    await wrapper.find('[data-testid="title-input"]').setValue(mockPost.title)
    await wrapper.find('[data-testid="body-input"]').setValue(mockPost.body)

    //submit the form
    await wrapper.find('[data-testid="post-form"]').trigger('submit')

    expect(wrapper.find('[type="submit"]').html()).toContain('Creating...')

    await flushPromises()

    // assert that the created post is displayed on screen
    expect(wrapper.html()).toContain(mockPost.title)
    expect(wrapper.html()).toContain(mockPost.body)
  })
});
```

### UI

- npm i --dev @vitest/ui
- `npm run test:unit -- --ui` ()




