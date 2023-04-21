---
title: SvelteKit + Tailwind Landing Page
created: '2022-10-21T11:44:03.787Z'
modified: '2022-10-22T11:03:39.348Z'
---

# SvelteKit + Tailwind Landing Page

- Portfolio Website with Tailwind CSS | Tailwind Tutorial for Beginners
 https://www.youtube.com/watch?v=4zHNGNCIezY
- https://blog.openreplay.com/exploring-sveltekit-in-2022-by-building-a-portfolio-website/
- Responsive Designs with Tailwind CSS
 https://www.youtube.com/watch?v=tcK38Simjaw

## Pomodoros:

21.10.2022 🍅🍅🍅🍅🍅🍅🍅🍅🍅🍅🍅

## Notes

VSCODE: Alt/Option + Click
Selects each instance with a new cursor

Best parts:

- More programmtic approach to Web Design, configurable
- Breakpoint prefixes like `hidden sm:block` or `sm:bg-orange-400` 

Other notes:

- `sm:bg-orange-400 md:bg-orange-600 lg:bg-orange-900` (https://tailwindcss.com/docs/responsive-design)
  - "Don't use sm: to target mobile devices", "Use unprefixed utilities to target mobile, and override them at larger breakpoints"  https://tailwindcss.com/docs/responsive-design#targeting-mobile-screens
- Selfhost google fonts: https://jeffpohlmeyer.com/self-hosting-a-font-with-tailwind-and-sveltekit, but used https://google-webfonts-helper.herokuapp.com/fonts
  - https://heyreliable.com/ultimate-google-font-pairings/ - thx!
- values which are not in config: https://tailwindcss.com/docs/adding-custom-styles#using-arbitrary-values

TODOs:

- [ ] Custom colors?
- [ ] Width in rems?
- [ ] How to properly size SVGs, such as bootstrap icons?
- [ ] How to use SCSS properly with @import? https://github.com/Sensei85/sveltekit-tailwind-sass-starterkit
- [ ] Try image transforming, https://kit.svelte.dev/docs/assets#transforming -> vite-imagetools , https://www.reddit.com/r/sveltejs/comments/mdd9ov/using_viteimagetools_with_sveltekit/
  - https://rodneylab.com/sveltekit-image-plugin/
- [ ] How to do dark mode?
