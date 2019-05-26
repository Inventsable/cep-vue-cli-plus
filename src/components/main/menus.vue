<template>
  <div></div>
</template>

<script>
// Invisible component that reactively handles flyout and context menus.
// All changes and modifications trigger redraw of menu and events.
// Modify either menu with .push() or other array methods and see results instantly

// Access this component anywhere via this.app.menus (this.$root.$children[0].menus)

export default {
  name: "menus",
  data: () => ({
    // this.app.menus.context
    context: {
      menu: [
        {
          id: "refresh",
          label: "Refresh panel",
          enabled: true,
          checkable: false,
          checked: false
        },
        { label: "---" },
        {
          id: "localhost",
          label: "Launch debug",
          enabled: true,
          checkable: false,
          checked: false
        }
      ]
    },
    // this.app.menus.context
    flyout: {
      menu: [
        {
          id: "refresh",
          label: "Refresh panel",
          enabled: true,
          checkable: false,
          checked: false
        }
      ]
    }
  }),
  computed: {
    app() {
      return this.$root.$children[0];
    },
    contextMenu() {
      return this.context.menu;
    },
    // Flyout menu converts to XML from reactive JSON in data() above
    flyoutMenu() {
      let str = `<Menu>`;
      this.flyout.menu.forEach(item => {
        if (item.id)
          str += `<MenuItem Id="${item.id}" Label="${item.label}" Enabled="${
            item.enabled
          }" Checked="${item.checked}" />`;
        else str += `<MenuItem Label="---" />`;
      });
      return (str += `</Menu>`);
    }
  },
  watch: {
    // Any updates to menu will trigger CEP to reset it and callback events
    contextMenu(menu) {
      this.setContextMenu();
    },
    flyoutMenu(menu) {
      this.setFlyoutMenu();
    }
  },
  mounted() {
    this.app.menus = this;
  },
  methods: {
    contextMenuClicked(id) {
      // Callback to handle any context menu event
      if (id == "refresh") {
        location.reload();
      } else if (id == "localhost") {
        cep.util.openURLInDefaultBrowser(this.app.identity.localhost);
      }
    },
    flyoutMenuClicked(evt) {
      // Callback to handle any flyout menu event
      const id = evt.data.menuId;
      if (id == "refresh") {
        location.reload();
      }
    },
    setContextMenu() {
      this.app.csInterface.setContextMenuByJSON(
        JSON.stringify(this.context),
        this.contextMenuClicked
      );
    },
    setFlyoutMenu() {
      this.app.csInterface.setPanelFlyoutMenu(this.flyoutMenu);
      this.app.csInterface.addEventListener(
        "com.adobe.csxs.events.flyoutMenuClicked",
        this.flyoutMenuClicked
      );
    },
    init() {
      this.setContextMenu();
      this.setFlyoutMenu();
    }
  }
};
</script>
