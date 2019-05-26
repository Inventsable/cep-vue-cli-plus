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
- [Vuetify](https://vuetifyjs.com/en/getting-started/quick-start) as CSS framework
- [Vue-CLI-3](https://cli.vuejs.org/) as Node.js tooling (webkit)
- Paginations via [Vue Router](https://router.vuejs.org/)
- Full typescript support for any app with pravdomil's Adobe types (same as writing .jsx scripts but access to host DOM as autocomplete while typing)
- Full [Material Design Icon](https://materialdesignicons.com/) support
- Various personal utility components that handle context/flyout menus, launching CEF debug, matching all host app styles and more

## Generated panel:

:file_folder: <span style="font-size: 20px;">your-panel-name</span>
<br>&nbsp;&nbsp;|\_\_&nbsp;:file_folder: <span style="font-size: 20px;">CSXS</span>
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|\_\_&nbsp;:page_facing_up: <span style="font-size: 20px;">manifest.xml</span>
<br>&nbsp;&nbsp;|\_\_&nbsp;:file_folder: <span style="font-size: 20px;">public</span>
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|\_\_&nbsp;:page_facing_up: <span style="font-size: 20px;">CSInterface.js</span>
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|\_\_&nbsp;:page_facing_up: <span style="font-size: 20px;">index.html (**Production:** used with `npm run build`)</span>
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|\_\_&nbsp;:page_facing_up: <span style="font-size: 20px;">index-dev.html (**Development:** used with `npm run serve`)</span>
<br>&nbsp;&nbsp;|\_\_&nbsp;:file_folder: <span style="font-size: 20px;">src</span>
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|\_\_&nbsp;:file_folder: <span style="font-size: 20px;">main (utility components)</span>
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|\_\_&nbsp;:file_folder: <span style="font-size: 20px;">host (.jsx and scripting files)</span>
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|\_\_&nbsp;:file_folder: <span style="font-size: 20px;">plugins (Vue-CLI-3 plugins)</span>
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|\_\_&nbsp;:file_folder: <span style="font-size: 20px;">views (Vue Router pages)</span>
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|\_\_&nbsp;:page_facing_up: <span style="font-size: 20px;">App.vue</span>
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|\_\_&nbsp;:page_facing_up: <span style="font-size: 20px;">main.js</span>
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|\_\_&nbsp;:page_facing_up: <span style="font-size: 20px;">router.js</span>
<br>&nbsp;&nbsp;|\_\_&nbsp;:page_facing_up: <span style="font-size: 20px;">.debug</span>
<br>&nbsp;&nbsp;|\_\_&nbsp;:page_facing_up: <span style="font-size: 20px;">.gitignore</span>
<br>&nbsp;&nbsp;|\_\_&nbsp;:page_facing_up: <span style="font-size: 20px;">package.json</span>
<br>&nbsp;&nbsp;|\_\_&nbsp;:page_facing_up: <span style="font-size: 20px;">package-lock.json</span>
<br>&nbsp;&nbsp;|\_\_&nbsp;:page_facing_up: <span style="font-size: 20px;">vue.config.js (Avoids `file not found` errors in `index.html` after `npm run build`)</span>
