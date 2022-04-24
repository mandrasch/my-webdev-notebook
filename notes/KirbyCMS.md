---
title: KirbyCMS
created: '2022-04-15T15:42:09.556Z'
modified: '2022-04-18T18:12:50.028Z'
---

# KirbyCMS


## Pomodoros 🍅

- 15.04.2022 🍅🍅🍅🍅🍅
- 16.04.2022 🍅🍅🍅🍅🍅

=> continue here: https://youtu.be/QwjX8JAwBws?t=2457
=> single tour templates, deploy via composer, add basemap feature, i18n, try kirby version, activate panel
=> add pipeline (node lts, install composer in pipeline, send via save sftp)

## Videos & notes

### [Kirby 3: How to build a website from scratch](https://www.youtube.com/watch?v=QwjX8JAwBws&t=61s)

- general
  - client projects are often started with organizing content in the `content/`-folder
  - folders are automatically transformed to routes, nested structures are possible
  - `site.txt` - global site content / vars
  - kirby default folders: `home/` and `error` as fallback
- templates
  - default fallback: `site/templates/default.php`
- listed pages (`content/2_contact`) vs. unlisted pages (`content`)
- Snippet => easy, just `<?php snippet('footer'); ?>`
- Templates, e.g. projects directory


## TODOs

- [ ] pagination, live search (ajax) ?!
- [ ] nested snippets?!
- [ ] What is the best way to work with git? Use dist folder (and ignore it) for laravel mix?
- [ ] Use bootstrap5
- [ ] Test block editor
- [ ] Try out version plugin / figure out deployment, staging, local
- [ ] Test local web fonts
- [ ] Test multi language
- [ ] Test cookies, ytube embeds and gmaps
- [ ] Test https://getkirby.com/plugins/arnoson/kirby-vite
- [ ] https://maurice-renck.de/de/tech/2021/automatische-beitragsbilder
