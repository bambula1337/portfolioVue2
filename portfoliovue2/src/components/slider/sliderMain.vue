<template>
  <div class="sliderMain">
    <div class="WelcomeText-wrapper">
      <WelcomeText :main="WelcomeText.main" :sub="WelcomeText.sub" />
    </div>
    <Slider :ProjectName="Slider.ProjectName" />

    <p class="view-all">View all projects</p>
  </div>
</template>

<script>
import WelcomeText from "@/components/welcomeText.vue";
import Slider from "@/components/slider/slider.vue";

export default {
  name: "SliderMain",
  components: {
    WelcomeText,
    Slider,
  },
  data() {
    return {
      WelcomeText: {
        main: "Projects",
        sub: "My non-commercials projects",
      },
      Slider: {
        ProjectName: "SKYBOX",
      },
    };
  },
};
</script>

<style lang="scss" scoped>
.sliderMain {
  background-image: url("../../assets/img/projects/bgmade.png");
  background-repeat: no-repeat;
  background-position: 10% 200%;
  & .WelcomeText-wrapper {
    @apply mb-20;
  }

  & .view-all {
    @apply flex justify-center mt-3;
    font-family: "Train One";
    font-size: 2.5rem;
  }
}
</style>