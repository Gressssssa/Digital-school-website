# Digital School Macedonia - Website

A static website for a digital/coding school in Macedonia. It has pages for the programs, team, student success stories, blog, contact, and privacy/legal information.

There is no backend. The main focus of the project is to have a professional-looking website that loads quickly and gives visitors the information they need, together with an easy way to get in touch.

The website is built using plain HTML, CSS and vanilla JavaScript. There are no frameworks or build tools, so there is nothing to install or set up. This also makes it easy to host and edit.

## Pages

* `index.html` - homepage
* `about.html` - about the school
* `programs.html` - available courses
* `team.html` - founders and instructors
* `success-stories.html` - student testimonials
* `blog.html` - blog posts
* `contact.html` - contact form and location
* `privacy.html` - privacy policy and cookie information

The header, navigation and footer are the same on all pages. Since the website is relatively small, they are just copied into each page instead of using a templating system.

## Styling

All styling is in `css/style.css`.

The colors are stored as CSS variables at the top of the file instead of using hex values everywhere. This makes it easier to change the colors of the whole website from one place.

The website also supports dark mode automatically based on the user's browser/OS settings. There is a light theme and a dark theme inside the `@media (prefers-color-scheme: dark)` section.

One important thing with the colors is the difference between `--color-ink` and `--color-navy`.

`--color-ink` is mainly used for text, so it changes between dark text in light mode and light text in dark mode.

`--color-navy` stays dark in both themes. It is used for elements that are supposed to always have a dark background, such as the logo badge, footer, CTA section, avatars and blog thumbnails.

Because of this, `--color-ink` shouldn't be used as a background for those elements. Otherwise, in dark mode the background could become light and the text wouldn't be readable.

## Multi-language (i18n)

The website supports three languages:

* English
* Albanian
* Macedonian

The translations are stored in:

* `locales/en.json`
* `locales/sq.json`
* `locales/mk.json`

All three files use the same keys, with only the translated text being different.

Text that needs to be translated uses a `data-i18n="key.here"` attribute in the HTML. `js/i18n.js` finds these elements and replaces the text with the translation for the selected language.

The selected language is saved in `localStorage` under `ds_lang`, so it stays selected when the user comes back to the website.

`js/i18n-data.js` is used for loading the language JSON files.

## Cookie Banner

There is a cookie consent banner at the bottom of the page. It asks the user about optional analytics/marketing cookies and also has a link to the privacy page for more information.

The banner only appears the first time. When the user chooses either **Accept all** or **Essential only**, the choice is saved in `localStorage` under `ds_cookie_consent` with either `all` or `necessary` as the value.

This is intentional, so the banner not appearing again is not a bug.

When testing it, the consent can be reset from:

**DevTools → Application → Local Storage → delete `ds_cookie_consent` → refresh**

## JavaScript

`main.js` handles the main interactive parts of the website:

* mobile navigation menu
* language dropdown
* cookie consent banner
* contact form validation//is this a readme file? 