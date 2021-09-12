---
title: H5P Tutorials - Oliver Tacke
created: '2021-09-12T13:55:30.254Z'
modified: '2021-09-12T16:01:22.251Z'
---

# H5P Tutorials - Oliver Tacke

by Oliver Tacke

## Pomodoros 🍅

- 12.09.2021 🍅🍅🍅

## H5P Tutorials Basics

https://www.youtube.com/watch?v=xEgBJaRUBGg

- Drupal 7 is currently recommended (https://h5p.org/development-environment#:~:text=H5P%20development%20does%20not%20require,make%20development%20a%20bit%20easier.), setup with DDEV:
https://ddev.readthedocs.io/en/stable/users/cli-usage/#drupal-67-quickstart

### Install Drupal 7 & DDEV

1. create new folder
2. paste the unzipped drupal7-download into it (https://www.drupal.org/project/drupal)
3. run `ddev config` (drupal7 will be recognized)
4. `ddev start`
5. Run `ddev launch`, navigate to /install.php
6. Select "Minimal"
7. Download H5P https://www.drupal.org/project/h5p
8. Unzip and paste it to `/modules`
7. Go to Administration > Modules > Enable H5P, H5P Editor
8. ⚠️ Click "Configure" for H5P, activate:
  8.1 "Enable H5P development mode"
  8.2 "Enable library development directory (for programers only)"

### Development folder

Located in `sites/default/files/h5p/development`, usage e.g:

```
cd sites/default/files/h5p/development
git clone https://github.com/otacke/h5p-dictation.git
```

### H5P CLI

https://h5p.org/h5p-cli-guide

- `npm install -g h5p`

### Try out with h5p-dictation

Lesson learned: **Install content types first via dashboard, add git repos in development/ afterwards! Otherwise dependencies will not be install automatically**

After `npm run install` & `npm run build`, I ran into the following adding the content type on website:

```
Missing dependency H5P.Question 1.4 required by H5P.Dictation 1.1.
Missing dependency H5P.JoubelUI 1.3 required by H5P.Dictation 1.1.
Missing dependency H5P.Audio 1.4 required by H5P.Dictation 1.1.
Missing dependency H5P.TextUtilities 1.3 required by H5P.Dictation 1.1.
...
```

Found this forum post (https://h5p.org/comment/43097#comment-43097):

- removed h5p-dictation/ temporarily from dev folder
- deleted installed library in https://h5p-drupal7-ddev.ddev.site/admin/content/h5p
- installed h5p-dictation the normal way
- re-added h5p-dictation/ in dev folder
- added alert() to /src/h5p-dictation.js, ran `npm run build` => now everything works :-)

### Bundle the file

```
cd ..
h5p pack h5p-dictation/ my-dictation.h5p
```

## H5P Tutorials: semantics.json

https://www.youtube.com/watch?v=UIGMqj_yN4A

- https://github.com/h5p/h5p-multi-choice/blob/master/semantics.json


## //TO-WATCH

- https://www.youtube.com/watch?v=3DrmXtkBErM
- https://www.youtube.com/watch?v=eKdNuqRw77o
- https://www.youtube.com/watch?v=HjtwjqJ6onk
- https://www.youtube.com/watch?v=hxk4JD_urMs&t=1s

