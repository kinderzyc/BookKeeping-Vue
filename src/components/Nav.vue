<template>
  <div class="nav">
    <router-link to="/lables">
      <Icon name="lables" />标签
    </router-link>
    <router-link to="/money">
      <Icon name="wallet" />记账
    </router-link>
    <router-link to="/statistics">
      <Icon name="charts" />统计
    </router-link>
  </div>
</template>

<script lang="ts">
// let importAll = (requireContext: __WebpackModuleApi.RequireContext) => requireContext.keys().forEach(requireContext);
//   try {importAll(require.context('../assets/icons', true, /\.svg$/));} catch (error) {console.log(error);}

// let importAll = (requireContext: __WebpackModuleApi.RequireContext) => requireContext.keys().forEach(requireContext);

export default {
  name: "Nav"
};
</script>

<style lang="scss" scoped>
.nav {
  border: 1px solid red;
}
</style>