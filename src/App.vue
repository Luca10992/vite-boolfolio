<script>
import AppHeader from "./components/AppHeader.vue";
import ProjectList from "./pages/ProjectList.vue";

export default {
  data() {
    return {};
  },
  components: { AppHeader, ProjectList },
};
</script>

<template>
  <app-header></app-header>
  <div class="container py-5">
    <router-view></router-view>
  </div>
</template>

<style lang="scss">
@use "./src/style/general.scss";
</style>
