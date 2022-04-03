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
  @apply mt-88;
  @apply smlger:mt-108;
  @apply lg:mt-32;
  @media (min-width: 1024px) {
    background-image: url("../../assets/img/projects/bgmade1.png");
    background-repeat: no-repeat;
    background-position: 10% 200%;
    background-size: 80rem;
  }

  @media (min-width: 1440px) {
    background-image: url("../../assets/img/projects/bgmade1.png");
    background-repeat: no-repeat;
    background-position: 10% 150%;
    background-size: 120rem;
  }

  & .WelcomeText-wrapper {
    @apply mb-10;
  }

  & .view-all {
    @apply flex justify-center text-3xl mt-5 text-center;
    @apply lg:mt-16;
    font-family: "Train One";
  }
}
</style>