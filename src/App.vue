

<script>
import { RouterLink, RouterView } from 'vue-router'
import Navigation from './components/Navigation.vue'
export default {
  name: "App",
  components: {
    Navigation
  }
}
</script>

<template>
  <div class="wrapper">
    <RouterView />
  </div>
</template>

<style>
.app {
  width: 100%;
}
</style>