---
title: CraftCMS
created: '2022-07-29T13:31:39.647Z'
modified: '2022-09-10T15:22:29.923Z'
---

# CraftCMS

https://craftquest.io/courses/real-world-craft-cms/44154

## Pomodoros 🍅

10.09.2022 🍅🍅🍅🍅
09.09.2022 🍅🍅🍅
02.09.2022 🍅
26.08.2022 🍅🍅
29.07.2022 🍅🍅🍅🍅
31.07.2022 🍅🍅🍅🍅

## (Possible) goals:

- [ ] Work through https://craftquest.io/courses/real-world-craft-cms 
    - [ ] Setup deployment via Github Action, Deployer, Ploi, Pipeline
    - [ ] Recommended before: [Craft 4 Quick Start](https://craftquest.io/courses/craft-cms-quick-start-guide/42973)
    - [ ] Train2Lake damit bauen

OLD: 
- [ ] Work through course CraftQuest - Coffeeshop website: https://www.youtube.com/watch?v=x5bVKZxFdPo&list=PLCy7dPypkr2rOlj9Ps5HbzYeJecL48yg-

- [ ] Understand new assets system in Craft 4: https://craftquest.io/courses/whats-new-in-craft-cms-4/41499

- [ ] Check if deployment is possible via Deployer v7 (like https://t3terminal.com/blog/typo3-gitlab-deployment/)
  - https://gist.github.com/mtwalsh/fce3c4aa416996e5900e8ac9f471dd6c
- [ ] Check support for `ddev pull`
- [ ] Check vite support in DDEV
    - https://craftquest.io/courses/ddev-and-craft-cms-quick-start-guide/43674
- [ ] Check if we can use Bootstrap5 + vite
- [ ] Check gitpod support
- [ ] Multi-Level-Navigation https://craftcookbook.net/recipes/search-results?q=multi+level

## Real World Craft CMS Course

- Course: https://craftquest.io/courses/real-world-craft-cms 
- Starter: https://github.com/CraftQuest/craft-starter-vite
- **My repo: https://github.com/mandrasch/craft4-trailquest-demo**



## Other notes

- https://craftcms.com/docs/getting-started-tutorial/install/

- Logs in `storage/logs`
- Dev Mode: Full debugging output ([Video](https://www.youtube.com/watch?v=PDU-7NxSXDo&list=PLCy7dPypkr2rOlj9Ps5HbzYeJecL48yg-&index=15))

```
# .env
# The environment Craft is currently running in (dev, staging, production, etc.)
CRAFT_ENVIRONMENT=dev
```

Is used in `config/general.php`:
```php
return GeneralConfig::create()
  // ...
  ->allowAdminChanges($isDev)
```

- Debugging via [Yii Debug Toolbar](https://www.youtube.com/watch?v=2lMSaN5wMaU&list=PLCy7dPypkr2rOlj9Ps5HbzYeJecL48yg-&index=16)


### Courses

- CraftQuest - Coffeeshop website: https://www.youtube.com/watch?v=x5bVKZxFdPo&list=PLCy7dPypkr2rOlj9Ps5HbzYeJecL48yg-
- Luke Peters: https://www.youtube.com/watch?v=XfAdPsKCIG4&list=PL4JDh0LtP7jqO_IsfzVDNGRKkkbXmrSFZ

- Reactive Components: https://putyourlightson.com/plugins/sprig

### Data types

Source: [Video](https://www.youtube.com/watch?v=CL26aqEldVY&list=PLCy7dPypkr2rOlj9Ps5HbzYeJecL48yg-&index=17)

- **Sections**
  - **Channel** (related entries like blog posts, recipes)
  - **Structure** (similiar to channel, but has hierachy, e.g. /about/offices and /about/offices/austin)
  - **Single** (for single pages, such as landing pages, typically with unique content which isn't shared)
- **Fields & Field Types**
  - Fields are not tied to Channels or Structures, but they can be organized in categories
- **Entries** (How content is stored in a section)
- **Templates** (Twig)

### Preview targets and view tokens

- Check out content on detail page, listings page, even homepage - that's nifty!
- View links with token can be shared (token will expire automatically) - that's nifty!

### Category groups

- Category (Region / City) <-> Entries (Channels, eg. Activity in City)

### Twig

- batch filter

- Laravel Collections are / can be used in craft 4 instead of twig filters? https://craftquest.io/articles/convenience-of-collections-in-craft-cms-4

## Pros

- craft cares about authoring experience, all label titles in the dashboard can be customized, helptexts can be displayed
- you can even customize all column tables for the dashboard out of the box (https://craftquest.io/courses/real-world-craft-cms/44662)! :-o

## Cons

- no current way of using prettier autoformatting in vscode?! :(((

### Accessibility

- https://craftcms.com/accessibility and blog entry https://craftcms.com/blog/accessibility, Craft 4 also introduced 
