<template>
  <div class="projects">
    <div class="welcometext-wrapper">
      <WelcomeText :main="WelcomeText.main" :sub="WelcomeText.sub" />
    </div>
    <Slider :ProjectName="Slider.ProjectName" />
  </div>
</template>

<script>
import WelcomeText from "@/components/welcomeText.vue";
import Slider from "@/components/slider/slider.vue";

export default {
  name: 'Projects',
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
      Slider: {
        ProjectName: 'SKYBOX',
        urls: [],
        IntervalTime: 9000,
      }
    };
  },
}
</script>

<style lang="scss" scoped>
.projects{
  & .welcometext-wrapper{
    @apply mb-10;
  }
}
</style>