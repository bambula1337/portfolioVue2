<template>
  <div class="header">
    <div class="logoWrapper">
      <router-link to="/" class="logo" :active-class="'active'"
        >adm’s</router-link
      >
    </div>
    <div class="links">
      <router-link to="/contact" class="link" :active-class="'active'"
        >about me</router-link
      >
      <router-link to="/contact" class="link" :active-class="'active'"
        >projects</router-link
      >
      <router-link to="/contact" class="link" :active-class="'active'"
        >contact</router-link
      >
    </div>
  </div>
</template>

<script>
export default {
  name: "Header",
};
</script>

<style lang="scss" scoped>
.header {
  background: url("../assets/img/header/background.png");
  background-size: 120rem;
  background-position: 70%, center;
  @apply flex justify-around bg-no-repeat overflow-hidden h-72;
  & .logoWrapper {
    & .logo {
      @apply text-5xl relative -left-24 top-2 text-white;
      font-family: "Train One";
    }
  }
  & .links {
    @apply flex relative -left-24;
    & .link {
      @apply mx-14 text-5xl text-white mt-4 h-10;
      font-family: "Zen Tokyo Zoo";
    }
  }
}
</style>