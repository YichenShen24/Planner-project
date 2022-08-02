<template>
  <TheHeader />
  <Navbar />
  <router-view />
</template>

<script>
import Navbar from "./components/Navbar.vue";
import TheHeader from "./layouts/TheHeader.vue";
import FilterNav from "./components/FilterNav.vue";

export default {
  components: { Navbar, TheHeader, FilterNav },
};
</script>
<style>
body {
  background: #f2f2f2;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #555;
  max-width: 600px;
  margin: 0 auto;
}
</style>
