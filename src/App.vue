<template>
  <div id="app" class="align-max-width">
    <Navigation />
    <Dashboard />
  </div>
</template>

<script>
import Dashboard from "./components/Dashboard.vue";
import Navigation from "./components/Navigation.vue";
import "./assets/base.scss";
export default {
  name: "App",
  components: {
    Dashboard,
    Navigation
  },
};
</script>

<style lang="scss" scoped>
@import "./assets/app.scss";
#app {
  @include desktopsmall{
    display: flex;
  }
}
</style>
