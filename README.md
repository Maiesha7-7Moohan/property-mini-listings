# property-mini-listings


This template should help get you started developing with Vue 3 in Vite.

## Recommended IDE Setup

[VS Code](https://code.visualstudio.com/) + [Vue (Official)](https://marketplace.visualstudio.com/items?itemName=Vue.volar) (and disable Vetur).

## Recommended Browser Setup

- Chromium-based browsers (Chrome, Edge, Brave, etc.):
  - [Vue.js devtools](https://chromewebstore.google.com/detail/vuejs-devtools/nhdogjmejiglipccpnnnanhbledajbpd)
  - [Turn on Custom Object Formatter in Chrome DevTools](http://bit.ly/object-formatters)
- Firefox:
  - [Vue.js devtools](https://addons.mozilla.org/en-US/firefox/addon/vue-js-devtools/)
  - [Turn on Custom Object Formatter in Firefox DevTools](https://fxdx.dev/firefox-devtools-custom-object-formatters/)

## Customize configuration

See [Vite Configuration Reference](https://vite.dev/config/).

## Project Setup

```sh
npm install
```

### Compile and Hot-Reload for Development

```sh
npm run dev
```

### Notes

- Open the project in a terminal that allows running `npm` (Command Prompt, Git Bash, or enable PowerShell execution policy).
- The dev server runs at `http://localhost:5173` by default.

### What I changed

- Added a small property listings SPA under `src/components/PropertyApp.vue`.
- New components: `src/components/PropertyCard.vue`, `src/components/HeaderBar.vue`.
- `src/views/HomeView.vue` now mounts the property app.

### Compile and Minify for Production

```sh
npm run build
```
