<template>
  <div id="app">
    <router-view />
  </div>
</template>

<script lang="ts">
import Vue from "vue";
export default Vue.extend({});
</script>

<style lang="scss">
@import "./assets/style/reset.scss";
@import "./assets/style/helper.scss";
body {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  line-height: 1.5;
  font-family: $font-black;
  font-size: 20px;
}
#app {
  max-width: 500px;
  margin: 0 auto;
}
</style>
