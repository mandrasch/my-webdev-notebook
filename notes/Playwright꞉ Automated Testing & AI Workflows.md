---
title: 'Playwright: Automated Testing & AI Workflows'
created: '2026-11-02T12:07:42.922Z'
modified: '2026-11-04T17:18:23.554Z'
---

# Playwright: Automated Testing & AI Workflows

https://master.dev/courses/playwright/ - Steve Kinney
(Also available: Testing Fundamentals, https://master.dev/courses/testing/)

## Pomodoros 🍅

02.03.2026 🍅
04.03.2026 🍅

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

