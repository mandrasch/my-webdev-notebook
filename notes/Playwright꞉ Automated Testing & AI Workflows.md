---
title: 'Playwright: Automated Testing & AI Workflows'
created: '2026-11-02T12:07:42.922Z'
modified: '2026-11-06T12:23:47.393Z'
---

# Playwright: Automated Testing & AI Workflows

https://master.dev/courses/playwright/ - Steve Kinney
(Also available: Testing Fundamentals, https://master.dev/courses/testing/)

- [ ] Apply to privat side projects like Karenz Wizard?
- [ ] Visual Regression? https://bsky.app/profile/paolo.ricciuti.me/post/3mzgbnpsut22l 
- [ ] How to apply this for a11y?
- [ ] check out https://e2e.com/ or similiar?  https://tester.army/ 

## Pomodoros 🍅

02.11.2026 🍅
04.11.2026 🍅
05.11.2026 🍅
06.11.2026 🍅

## Notes

Official: https://stevekinney.com/courses/self-testing-ai-agents

- Pyramid, top to bottom:
  - End to End: "Simulate real user scenarios from start to finish to verify that the entire application workflow functions properly across all components and integrated systems."
  - Integration: Validate how different modules or subsystems work together to ensure that data flows correctly between combined components.
  - Unit Tests: Focus on verifying the smallest isolated units of code, such as individual functions or methods, in complete isolation from external dependencies.

  https://stevekinney.com/courses/self-testing-ai-agents/the-testing-pyramid-as-a-feedback-hierarchy 

### Testing Strategies with AI

- specific commands, file paths, API, etc.
  - run npm run test before declaring done
  - write a failing test before the implementation
  - read tracer at playwright-report/trace.zip before guessing
  - never use page.waitForTimeout - use waitForResponse or getByRole
  - green = lint + typecheck + test + test:e2e all exit zero
- or "definition of done" in CLAUDE.md, etc.

### Playwright UI:

- visual GUI `npx playwright test --ui` (not used in course)

### Playwright: Locators

https://stevekinney.com/courses/self-testing-ai-agents/locators-and-the-accessibility-hierarchy

The six main locators are: 
- getByRole (uses accessibility tree)
- getByLabel (works with form elements)
- getByPlaceholder (on input fields)
- getByText (searches DOM for text)
- getByTestId (custom data attributes)
- and locator (CSS selectors).

#### Auto-Wait/Retry in assertions

> Playwright gives you Web-First Assertions with convenience methods for creating assertions that will wait and retry until the expected condition is met. (...)
> By default, the timeout for assertions is set to 5 seconds.
https://playwright.dev/docs/api/class-playwrightassertions

- https://playwright.dev/docs/api/class-locatorassertions#locator-assertions-to-be-visible (also has a timeout option, optional)

```
test('add to shelf button exists', async ({ page }) => {
	await page.goto('/playground');

	await expect(page.getByRole('button', { name: 'Add to shelf' })).toBeVisible();
});
```

#### Challenges

https://stevekinney.com/courses/self-testing-ai-agents/lab-locator-challenges

- Localization / localized strings?
  - Set test browser to anything you want
  - i18n libs --> read out languages and keys from the language files

##### Getting selectors: ui and codegen recording mode

- `--ui` mode has the Locator info as well on elements
- `npx playwright codegen http://localhost:5173` - opens up a ui with locator / recording

##### toMatchAriaSnapshot()

- toMatchSnapshot in jest, vitest, etc. - css can be changed, but a11y tree is not changed = great for validating that no function was changed




