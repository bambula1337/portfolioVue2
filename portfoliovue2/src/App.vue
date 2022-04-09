<template>
  <div id="app" :class="{'bg-gray': $route.name == 'Projects'}">
    <Header />
    <div class="main">
      <router-view />
    </div>
    <Footer />
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
// Tailwind Connection
@import "./assets/styles/tailwind.scss";
// Fonts Connection
@import url("https://fonts.googleapis.com/css2?family=Comfortaa:wght@700&family=Train+One&family=Ubuntu&family=Zen+Tokyo+Zoo&display=swap");

// Scroll Style
::-webkit-scrollbar {
  width: 0.6vw;
}

::-webkit-scrollbar-track {
  background-color: rgb(176, 176, 176);
}

::-webkit-scrollbar-thumb {
  background-color: rgb(129, 129, 129);
  border-radius: 30px;
}

::-webkit-scrollbar-thumb:hover {
  background-color: rgb(110, 110, 110);
}


//For Correct peview header with footer

.main {
  @apply min-h-screen;
}

//For Project Page

.bg-gray{
  background-color: rgb(190, 190, 190);
}
</style>
