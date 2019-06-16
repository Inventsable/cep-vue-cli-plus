<template>
  <v-app dark>
    <notification :text="notification.text" :color="notification.color"/>
    <stylizer/>
    <identity/>
    <menus/>
    <navbar v-if="hasNavbar"/>
    <alert/>
    <v-content :style="getContentStyle()">
      <router-view/>
    </v-content>
    <version/>
    <loadingscreen/>
  </v-app>
</template>

<script>
import identity from "./components/main/identity.vue";
import stylizer from "./components/main/stylizer.vue";
import menus from "./components/main/menus.vue";
import alert from "./components/main/alert";
import notification from "./components/main/notification.vue";
import navbar from "./components/main/navbar.vue";
import loadingscreen from "./components/main/loadingscreen.vue";
import version from "./components/main/version.vue";

export default {
  name: "App",
  components: {
    identity,
    notification,
    stylizer,
    navbar,
    menus,
    version,
    loadingscreen,
    alert
  },
  computed: {
    storage() {
      return window.localStorage;
    }
  },
  data: () => ({
    csInterface: null,
    identity: null,
    stylizer: null,
    progress: null,
    loadingscreen: null,
    navbar: null,
    menus: null,
    hasNavbar: true,
    notification: {
      text: "Extension is mounted",
      color: "primary",
      state: false
    },
    home: null,
    isMounted: false
  }),
  mounted() {
    console.clear();
    this.csInterface = new CSInterface();
    this.csInterface.addEventListener("console", this.consoler);

    // Utility components are already mounted prior to this

    console.log(
      `${this.identity.extName} ${this.identity.extVersion} : ${
        this.identity.isDev ? "DEV" : "BUILD"
      }`
    );
    this.isMounted = true;

    this.loadUniversalScripts();

    // Vue Router must be manually initialized in CEP:
    this.$router.push({ name: "home" });
  },
  methods: {
    dispatchEvent(name, data) {
      var event = new CSEvent(name, "APPLICATION");
      event.data = data;
      this.csInterface.dispatchEvent(event);
    },
    getContentStyle() {
      // Sets height of <v-content> and "page" element.
      // This is done to allow for interchangeable main content with certain universal components (e.g. toolbars like <navbar>)
      return `
        overflow: auto;
        margin-top: ${
          this.$route.name == "home"
            ? this.hasNavbar
              ? this.getCSS("toolbar-height") - 2
              : "0"
            : "0"
        }px;
        padding: 0px 0px 0px 0px;
        max-height: calc(100vh - ${
          this.hasNavbar ? this.getCSS("toolbar-height") : "0"
        }px);
      `;
    },
    loadScript(path) {
      this.csInterface.evalScript(`$.evalFile('${path}')`);
    },
    loadUniversalScripts() {
      // Preloads universal scripts and main host script file
      this.loadScript(`${this.identity.root}/src/host/universal/json2.jsx`);
      this.loadScript(`${this.identity.root}/src/host/universal/Console.jsx`);
      this.loadScript(
        `${this.identity.root}/src/host/${this.identity.appName}/host.jsx`
      );
    },
    consoler(msg) {
      // Catches all console.log() usage in .jsx files via CSEvent
      console.log(`${this.identity.appName}: ${msg.data}`);
    },
    getCSS(prop) {
      // Returns current value of CSS variable
      // prop == typeof String as name of variable, with or without leading dashes:
      // this.getCSS('color-bg') || this.getCSS('--scrollbar-width')
      return window
        .getComputedStyle(document.documentElement)
        .getPropertyValue(`${/^\-\-/.test(prop) ? prop : "--" + prop}`);
    },
    setCSS(prop, data) {
      // Sets value of CSS variable
      // prop == typeof String as name of variable, with or without leading dashes:
      // this.setCSS('color-bg', 'rgba(25,25,25,1)') || this.setCSS('--scrollbar-width', '20px')
      document.documentElement.style.setProperty(
        `${/^\-\-/.test(prop) ? prop : "--" + prop}`,
        data
      );
    }
  }
};
</script>


<style>
:root {
  --toolbar-height: 40;

  --quad: cubic-bezier(0.48, 0.04, 0.52, 0.96);
  --quart: cubic-bezier(0.76, 0, 0.24, 1);
  --quint: cubic-bezier(0.84, 0, 0.16, 1);
}
</style>