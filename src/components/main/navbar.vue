<template>
  <div>
    <!-- Toolbar element existing outside of route -->
    <progressbar/>
    <div>
      <!-- https://vuetifyjs.com/en/components/toolbars#toolbar -->
      <v-toolbar app card dark class="darkToolbar">
        <v-toolbar-title>{{$route.name}}</v-toolbar-title>
        <v-spacer></v-spacer>

        <!-- https://vuetifyjs.com/en/components/buttons#button -->
        <v-btn v-for="(button, key) in buttons" :key="key" @click="goToLink(button.link)" icon flat>
          <v-icon>{{button.icon}}</v-icon>
        </v-btn>
      </v-toolbar>
    </div>
  </div>
</template>

<script>
import progressbar from "./progress";

export default {
  name: "navbar",
  components: {
    progressbar
  },
  data: () => ({
    buttons: [
      {
        icon: "mdi-vuetify",
        link: "https://vuetifyjs.com/en/components/toolbars#toolbar"
      }
    ]
  }),
  computed: {
    app() {
      return this.$root.$children[0];
    }
  },
  mounted() {
    this.app.navbar = this;
    const toolbar_content = document.querySelector(".v-toolbar__content");
    toolbar_content.style.height = `${this.app.getCSS("toolbar-height")}px`;
  },
  methods: {
    goToLink(link) {
      cep.util.openURLInDefaultBrowser(link);
    }
  }
};
</script>

<style>
.darkToolbar,
.theme--dark.v-system-bar,
.theme--dark.v-toolbar {
  background-color: var(--color-input-idle);
  cursor: default;
}
</style>
