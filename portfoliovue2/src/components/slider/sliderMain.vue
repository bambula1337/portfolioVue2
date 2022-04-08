<template>
  <div class="sliderMain" id="projects">
    <div class="WelcomeText-wrapper">
      <WelcomeText :main="WelcomeText.main" :sub="WelcomeText.sub" />
    </div>
    <Slider :ProjectName="Slider.ProjectName" />
    <router-link to="projects">
      <p class="view-all" @click="scrollTop">View all projects</p>
    </router-link>
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
  methods:{
    scrollTop: function(){
      window.scrollTo({
        top: 0,
        behavior: 'smooth',
      });
    }
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
  @media (min-width: 1280px) {
    background-image: url("../../assets/img/projects/bgmade1.png");
    background-repeat: no-repeat;
    background-position: 10% 200%;
    background-size: 100rem;
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
    @apply justify-center text-3xl mt-5 text-center flex items-center flex-col;
    @apply lg:mt-16;
    font-family: "Train One";

    &::after{
        @apply w-0 transition-all duration-1000;
        content: '';
        border-top: 2px black solid;
      }

      &:hover::after{
        @apply w-68;
      }
  }
}
</style>