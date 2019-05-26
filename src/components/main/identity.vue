<template>
  <div></div>
</template>

<script>
// Invisible component that auto-populates data about itself, the host app, and sibling extensions
// Access this component anywhere via this.app.identity (this.$root.$children[0].identity)

export default {
  name: "identity",
  data: () => ({
    isMounted: false
  }),
  computed: {
    app() {
      return this.$root.$children[0];
    },
    root() {
      return this.isMounted
        ? this.app.csInterface.getSystemPath(SystemPath.EXTENSION)
        : null;
    },
    localhost() {
      if (this.isMounted) {
        const debug = window.cep.fs.readFile(`${this.root}/.debug`);
        const port = new RegExp(
          `\\<Host\\sName\\=\\"${this.appName}\\"\\sPort\\=\\"(\\d*)`
        );
        return `http://localhost:${debug.data.match(port)[1]}`;
      }
    },
    isDev() {
      return this.isMounted ? /localhost/.test(document.location.href) : null;
    },
    extVersion() {
      if (this.isMounted) {
        const xml = window.cep.fs.readFile(
          `${this.activeExt.basePath}/CSXS/manifest.xml`
        );
        const verID = /ExtensionBundleVersion\=\"(\d|\.)*(?=\")/;
        const match = xml.data.match(verID);
        if (match && match.length) return match[0].replace(/\w*\=\"/, "");
        else return "unknown";
      }
    },
    appName() {
      return this.isMounted
        ? this.app.csInterface.hostEnvironment.appName
        : null;
    },
    appLocale() {
      return this.isMounted
        ? JSON.parse(window.__adobe_cep__.getHostEnvironment()).appLocale
        : null;
    },
    appVersion() {
      return this.isMounted
        ? JSON.parse(window.__adobe_cep__.getHostEnvironment()).appVersion
        : null;
    },
    userAgent() {
      return this.isMounted
        ? this.app.csInterface.getOSInformation("--user-agent")
        : null;
    },
    cepVersion() {
      return this.isMounted
        ? `${JSON.parse(window.__adobe_cep__.getCurrentApiVersion()).major}.${
            JSON.parse(window.__adobe_cep__.getCurrentApiVersion()).minor
          }.${JSON.parse(window.__adobe_cep__.getCurrentApiVersion()).micro}`
        : null;
    },
    hostCapabilities() {
      return this.isMounted
        ? JSON.parse(window.__adobe_cep__.getHostCapabilities())
        : null;
    },
    userId() {
      return this.isMounted ? window.__adobe_cep__.getCurrentImsUserId() : null;
    },
    extID() {
      return this.isMounted ? window.__adobe_cep__.getExtensionId() : null;
    },
    exts() {
      return this.isMounted
        ? JSON.parse(window.__adobe_cep__.getExtensions())
        : null;
    },
    activeExt() {
      return this.isMounted
        ? this.exts.find(ext => {
            return ext.id == this.extID;
          })
        : null;
    },
    extName() {
      return this.activeExt.name ? this.activeExt.name : null;
    }
  },
  mounted() {
    this.app.identity = this;
  },
  methods: {
    init() {
      this.isMounted = true;
      this.app.identity = this;
      console.log("Identity mounted:");
      console.log(this.activeExt);
    },
    checkHost() {
      this.exts.forEach(ext => {
        this.getExtData(ext.id);
      });
    },
    getExtData(id) {
      const target = this.exts.find(ext => {
        return ext.id == id;
      });
      const vr = this.getVersion(target);
      console.log(`${target.windowType}: ${target.name} v${vr}`);
    },
    getVersion(ext) {
      if (this.isMounted) {
        const xml = window.cep.fs.readFile(`${ext.basePath}/CSXS/manifest.xml`);
        const verID = /ExtensionBundleVersion\=\"(\d|\.)*(?=\")/;
        const match = xml.data.match(verID);
        return match && match.length
          ? match[0].replace(/\w*\=\"/, "")
          : "unknown";
      }
    }
  }
};
</script>
