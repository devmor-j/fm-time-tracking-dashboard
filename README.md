# Frontend Mentor - Time tracking dashboard solution

This is my solution to the [Time tracking dashboard challenge on Frontend Mentor](https://www.frontendmentor.io/challenges/time-tracking-dashboard-UIQ7167Jw). Frontend Mentor challenges help you improve your coding skills by building realistic projects.

## Table of contents

- [Overview](#overview)
  - [The challenge](#the-challenge)
  - [Screenshot](#screenshot)
  - [Links](#links)
- [My process](#my-process)
  - [Built with](#built-with)
  - [What I learned](#what-i-learned)
  - [Continued development](#continued-development)
  - [Useful resources](#useful-resources)
- [Author](#author)

## Overview

### The challenge

Users should be able to:

- View the optimal layout for the site depending on their device's screen size
- See hover states for all interactive elements on the page
- Switch between viewing Daily, Weekly, and Monthly stats

### Screenshot

Designed with responsiveness in mind. Mobile-first developement means this project was styled for small screens with a `flexbox stack layout'. Tablet breakpoint is on 768px which means that screens larger than that will view the`grid layout`.

Desktop [1536px]

![Desktop](./screenshots/Desktop%20%5B1536px%5D%20Time%20tracking%20dashboard.webp)

Mobile [375px] iPhone 5/SE

![Mobile](./screenshots/Mobile%20%5B375px%5D%20Time%20tracking%20dashboard.webp)

### Links

- Solution URL: [Github repository](https://github.com/devmor-j/fm-time-tracking-dashboard)
- Live Site URL: [Hosted on Github Pages](https://devmor-j.github.io/fm-time-tracking-dashboard/)

## My process

### Built with

- Semantic HTML5 markup
- Mobile-first workflow
- CSS custom properties + Flexbox and Grid
- [Vue.js 3](https://vuejs.org/) - The Progressive JavaScript Framework
- [TypeScript](https://www.typescriptlang.org/) - TypeScript is JavaScript with syntax for types
- [Vite.js](https://vitejs.dev/) - Next Generation Frontend Tooling
- [Modern Css Reset](https://github.com/hankchizljaw/modern-css-reset) - One of the best resetters
- [SASS](https://sass-lang.com) - CSS with superpowers
- [CSS Modules](https://github.com/css-modules/css-modules) - A CSS Module is a CSS file in which all class names and animation names are scoped locally by default
- [ESLint](https://eslint.org/) - Find and fix problems in your JavaScript code
- [Prettier](https://prettier.io/) - Opinionated Code Formatter

### Further development

If you wanna work on a new feature try adding transition on tracking cards when profile timeframe changes.

Another feature would be showing 'zero' instead of `0hrs` which I already implemented but you can clone this repo and strat from scratch.

If you like to debug and refactor css then try to drop css modules and use native vue scoped styles.

One more task for css development is to drop dependency for `css-modern-reset` which I don't recommend personally but if you hate css magics then this will make you write all those hidden reset styles.

### Useful resources

- [Dynamic image source `<img :src="..." />` not working](https://stackoverflow.com/questions/40491506/vue-js-dynamic-images-not-working) - Note that setting your img src via v-bind (`:{property}`) does not work in vite build process. instead put your images in `public` folder. [another discussion](https://forum.vuejs.org/t/dynamic-img-src-of-item-in-for-loop/119695)

- [ISO 8601 Duration in JavaScript](https://www.twilio.com/blog/parse-iso8601-duration-javascript) - Helps robots to know this app is about time and also Google will love this semantic tag:

  ```html
  <time datetime="..."><time/>
  ```

  An example will be `datetime="PT36H"` witch means 36 hours duration. If you're interested in working with this type of time then refer to [TinyDuration](https://github.com/MelleB/tinyduration) and [MDN docs](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/time).

## Author

- Frontend Mentor - [@devmor-j](https://www.frontendmentor.io/profile/devmor-j)
