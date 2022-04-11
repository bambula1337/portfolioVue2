<template>
  <div class="projects">
    <div class="welcometext-wrapper">
      <WelcomeText :main="WelcomeText.main" :sub="WelcomeText.sub" />
    </div>
    <Slider
    v-for="(slider, index) in Slider"
    :key="index"
      :ProjectName="slider.ProjectName"
      :Slides="slider.urls"
      :IntervalTime="slider.IntervalTime"
      :IntervalAbility="slider.IntervalAbility"
    />
  </div>
</template>

<script>
import WelcomeText from "@/components/welcomeText.vue";
import Slider from "@/components/slider/slider.vue";

export default {
  name: "Projects",
  components: {
    Slider,
    WelcomeText,
  },
  data() {
    return {
      WelcomeText: {
        main: "All Projects",
        sub: "My all non-commercials projects",
      },
      Slider: [
        {
          id: 1,
          ProjectName: "SKYBOX",
          urls: [
            "/img/slider/skybox/SkyboxSlider_1.png",
            "/img/slider/skybox/SkyboxSlider_2.png",
            "/img/slider/skybox/SkyboxSlider_3.png",
            "/img/slider/skybox/SkyboxSlider_4.png",
          ],
          IntervalTime: 15000,
          IntervalAbility: true,
        },
      ],
    };
  },
};
</script>

<style lang="scss" scoped>
.projects {
  & .welcometext-wrapper {
    @apply mb-10;
  }
}
</style>