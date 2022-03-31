<template>
  <div id="app">
    <Header />
    <div class="main">
      <router-view />
    </div>
    <Footer/>
  </div>
</template>

<script>
import Header from "@/components/header.vue";
import Footer from "@/components/footer.vue";

export default {
  name: "App",
  components: {
    Header,
    Footer,
  },
};
</script>


<style lang="scss">
@import "./assets/styles/tailwind.scss";
@import url('https://fonts.googleapis.com/css2?family=Comfortaa:wght@700&family=Train+One&family=Ubuntu&family=Zen+Tokyo+Zoo&display=swap');

</style>
