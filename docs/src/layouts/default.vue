<template>
  <div id="app">
    <app-header @toggle-drawer="toggleDrawer()" />
    <div
      class="sidemenu__backdrop"
      v-if="showDrawer"
      @click="toggleDrawer()"
    ></div>
    <side-menu :show-drawer="showDrawer" @toggle-drawer="toggleDrawer()" />
    <div class="child">
      <nuxt-child />
    </div>
    <!-- <Nuxt /> -->
  </div>
</template>

<script>
import "../../../plugui.scss";
import "light-icons/dist/light-icon.css";

import AppHeader from "@/components/layout/AppHeader.vue";
import SideMenu from "@/components/layout/SideMenu.vue";

export default {
  components: {
    AppHeader,
    SideMenu,
  },
  data() {
    return {
      showDrawer: false,
    };
  },
  methods: {
    toggleDrawer() {
      this.showDrawer = !this.showDrawer;
    },
  },
};
</script>

<style lang="scss">
@import "./overwrite.scss";
@import "./examples.scss";
* {
  padding: 0px;
  margin: 0px;
  box-sizing: border-box;
}
a {
  text-decoration: none;
}

body,
#app {
  background-color: #f5f8fa;
  color: #566d79;
  font-family: Roboto, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

// Media Queries
@media only screen and (max-width: 600px) {
  #app {
    padding: 20px;
  }
  .bg-gray {
    div {
      padding: 0.5rem 1rem;
      border-radius: 4px;
    }
  }
}
.child {
  position: absolute;
  left: 250px;
  top: 55px;
  padding: 30px;
  z-index: -10000;
  width: calc(100% - 250px);
}

.feature-intro p {
  opacity: 0.8;
  line-height: 20px;
  margin: 8px 0px;
}
.sidemenu__backdrop {
  z-index: 998;
  background-color: rgba(28, 39, 45, 0.55);
  height: 100vh;
  width: 100vw;
  position: fixed;
  top: 0px;
  left: 0px;
  display: none;
  opacity: 0;
  transition: all 0.2s ease-in-out;
}

@media (max-width: 769px) {
  .child {
    left: 0px;
    width: 100%;
  }
  .sidemenu__backdrop {
    opacity: 1;
    display: initial;
  }
}
</style>
