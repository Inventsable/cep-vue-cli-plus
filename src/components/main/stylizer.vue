<template>
  <div></div>
</template>

<script>
// Invisible component which handles app theme and styling. All colors are based on CSS variables at :root,
// which this component will dynamically change (reflecting throughout the rest of the app)
// Access this component anywhere via this.app.stylizer (this.$root.$children[0].stylizer)

import toHex from "../../utils/color/toHex.js";
export default {
  name: "stylizer",
  data: () => ({
    theme: null,
    isMounted: false
  }),
  computed: {
    app() {
      return this.$root.$children[0];
    }
  },
  mounted() {
    this.app.stylizer = this;
  },
  methods: {
    init() {
      if (!this.isMounted) {
        this.app.csInterface.addEventListener(
          "com.adobe.csxs.events.ThemeColorChanged",
          this.appThemeChanged
        );
        this.appThemeChanged();
        this.isMounted = true;
      }
    },
    appThemeChanged() {
      const skinInfo = window.__adobe_cep__.getHostEnvironment();
      this.findTheme(JSON.parse(skinInfo).appSkinInfo);
    },
    findTheme(appSkin) {
      const bgcolor = appSkin.panelBackgroundColor.color;
      if (this.app.identity.appName !== "AEFT") {
        if (bgcolor.red > 230) this.theme = "lightest";
        else if (bgcolor.red > 170) this.theme = "light";
        else if (bgcolor.red > 80) this.theme = "dark";
        else this.theme = "darkest";
        this.assignTheme();
      } else if (this.app.identity.appName == "AEFT") {
        this.setGradientTheme(appSkin);
      }
    },
    assignTheme() {
      console.log(`${this.app.identity.appName} theme is ${this.theme}`);
      //  this.$root.activeTheme;
      //   console.log("Assigning theme...");
      // for (var i = 0; i < this.cssOrder.length; i++) {
      //     let prop = this.cssOrder[i], value = this.styleList[app][theme][i];
      //     if (!/width|radius/.test(prop)) {
      //     this.$root.setCSS(`color-${prop}`, value);
      //     } else {
      //     this.$root.setCSS(prop, value);
      //     }
      // }
    },
    setGradientTheme(appSkin) {
      const bgcolor = appSkin.panelBackgroundColor.color;
      this.app.setCSS("color-bg", this.toHex(bgcolor));
      this.app.setCSS("color-dark", this.toHex(bgcolor, -15));
      this.app.setCSS("color-input-idle", this.toHex(bgcolor, -12));
      this.app.setCSS("color-icon", this.toHex(bgcolor, 30));
      this.app.setCSS("color-button-disabled", this.toHex(bgcolor, 20));
      this.app.setCSS("color-scrollbar", this.toHex(bgcolor, -5));
      this.app.setCSS("color-scrollbar-thumb", this.toHex(bgcolor, 18));
      this.app.setCSS("color-scrollbar-thumb-hover", this.toHex(bgcolor, 35));
      this.app.setCSS("input-border-radius", "5px");
    }
  }
};
</script>
