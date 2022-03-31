<template>
  <div id="app">
    <div class="header"></div>
    <div class="main">
      <router-view />
    </div>
    <div class="footer"></div>
  </div>
</template>

<script>
export default {
  name: "App",
};
</script>


<style lang="scss">
@import "./assets/styles/tailwind.scss";
</style>
