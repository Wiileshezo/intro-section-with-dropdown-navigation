<template>
  <the-navigation></the-navigation>
  <RouterView />
  <the-footer></the-footer>
</template>

<script>
import { RouterLink, RouterView } from "vue-router";
import TheNavigation from "./components/TheNavigation.vue";
import TheFooter from "./components/TheFooter.vue";
export default {
  components: {
    TheNavigation,
    TheFooter,
  },
};
</script>

<style scoped></style>
