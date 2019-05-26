# cep-vue-cli-plus

## Boilerplate to be used for upcoming Yeoman generator

```bash
# future usage:
npm install yo
npm install generator-cep-vue-cli

yo cep-vue-cli-plus
```

## No setup required for:

- [Vue](https://vuejs.org/) as JS framework
- Hot Reloading (panel updates instantly on every save during `npm run serve`)
- [Vuetify](https://vuetifyjs.com/en/getting-started/quick-start) as CSS framework
- [Vue-CLI-3](https://cli.vuejs.org/) as Node.js tooling (webkit)
- Paginations via [Vue Router](https://router.vuejs.org/)
- Full typescript support for any app with pravdomil's Adobe types (same as writing .jsx scripts but access to host DOM as autocomplete while typing)
- Full [Material Design Icon](https://materialdesignicons.com/) support
- Various personal utility components that handle context/flyout menus, launching CEF debug, matching all host app styles and more

## Generated panel:

:file_folder: your-panel-name
<br>&nbsp;&nbsp;|\_\_&nbsp;:file_folder: CSXS
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|\_\_&nbsp;:page_facing_up: manifest.xml
<br>&nbsp;&nbsp;|\_\_&nbsp;:file_folder: public
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|\_\_&nbsp;:page_facing_up: CSInterface.js
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|\_\_&nbsp;:page_facing_up: index.html (**Production:** used with `npm run build`)
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|\_\_&nbsp;:page_facing_up: index-dev.html (**Development:** used with `npm run serve`)
<br>&nbsp;&nbsp;|\_\_&nbsp;:file_folder: src
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|\_\_&nbsp;:file_folder: [components](#components)
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|\_\_&nbsp;:file_folder: main (utility)
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|\_\_&nbsp;:file_folder: HelloWorld.vue
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|\_\_&nbsp;:file_folder: [host (.jsx and scripting files)](#scripting)
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|\_\_&nbsp;:file_folder: plugins (Vue-CLI-3 plugins)
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|\_\_&nbsp;:file_folder: views (Vue Router pages)
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|\_\_&nbsp;:page_facing_up: App.vue
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|\_\_&nbsp;:page_facing_up: main.js
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|\_\_&nbsp;:page_facing_up: router.js
<br>&nbsp;&nbsp;|\_\_&nbsp;:page_facing_up: .debug
<br>&nbsp;&nbsp;|\_\_&nbsp;:page_facing_up: .gitignore
<br>&nbsp;&nbsp;|\_\_&nbsp;:page_facing_up: package.json
<br>&nbsp;&nbsp;|\_\_&nbsp;:page_facing_up: package-lock.json
<br>&nbsp;&nbsp;|\_\_&nbsp;:page_facing_up: vue.config.js (Avoids `file not found` errors in `index.html` after `npm run build`)

## Components

:file_folder: ./src/components/main
<br>&nbsp;&nbsp;|\_\_&nbsp;:file_folder: main
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|\_\_&nbsp;:page_facing_up: alert.vue
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; • Test
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|\_\_&nbsp;:file_folder: identity.vue
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; • Test
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|\_\_&nbsp;:file_folder: loadingscreen.vue
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; • Test
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|\_\_&nbsp;:file_folder: menus.vue
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; • Test
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|\_\_&nbsp;:file_folder: navbar.vue
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; • Test
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|\_\_&nbsp;:page_facing_up: notification.vue
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; • Test
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|\_\_&nbsp;:page_facing_up: progress.vue
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; • Test
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|\_\_&nbsp;:page_facing_up: stylizer.vue
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; • Test
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|\_\_&nbsp;:page_facing_up: version.vue
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; • Test
<br>&nbsp;&nbsp;|\_\_&nbsp;:page_facing_up: HelloWorld.vue

## Scripting

:file_folder: ./src/host (only apps included on generate command will appear below)
<br>&nbsp;&nbsp;|\_\_&nbsp;:file_folder: universal
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|\_\_&nbsp;:page_facing_up: Console.jsx
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|\_\_&nbsp;:page_facing_up: json2.jsx
<br>&nbsp;&nbsp;|\_\_&nbsp;:file_folder: ILST
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|\_\_&nbsp;:page_facing_up: host.ts
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|\_\_&nbsp;:page_facing_up: host.jsx
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|\_\_&nbsp;:page_facing_up: tsconfig.json
<br>&nbsp;&nbsp;|\_\_&nbsp;:file_folder: AEFT
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|\_\_&nbsp;:page_facing_up: host.ts
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|\_\_&nbsp;:page_facing_up: host.jsx
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|\_\_&nbsp;:page_facing_up: tsconfig.json
<br>&nbsp;&nbsp;|\_\_&nbsp;:file_folder: PHXS
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|\_\_&nbsp;:page_facing_up: host.ts
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|\_\_&nbsp;:page_facing_up: host.jsx
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|\_\_&nbsp;:page_facing_up: tsconfig.json
