<template>
  <div class="slider">
    <div class="slider_and_name">
      <p class="project-name">{{ ProjectName }}</p>
      <div class="slider-wrapper">
        <SliderItem
          v-for="(slide, index) in slides"
          :key="index"
          :slideImgSrc="slide"
          :currentSlideID="currentSlideID"
          :index="index"
          :effect="effect"
        />
        <div class="sliderDots">
          <p
            v-for="(dot, index) in slides"
            :key="index"
            @click="switchTo(index)"
            :class="[currentSlideID == index ? 'active' : 'all']"
          ></p>
        </div>
      </div>
      <a
        href="https://github.com/bambula1337/CopyProIdea"
        class="github"
        ><img src="@/assets/img/slider/github_icon.png" alt=""
      /></a>
    </div>
    <SliderController
      @prev="prev"
      @next="next"
      :currentslidenumber="currentSlideID + 1"
      :totalslides="slides.length"
    />
  </div>
</template>

<script>
import SliderItem from "@/components/slider/sliderItem.vue";
import SliderController from "@/components/slider/sliderController.vue";

export default {
  name: "SliderComponent",
  components: {
    SliderItem,
    SliderController,
  },
  methods: {
    prev: function () {
      if (this.clickable) {
        this.currentSlideID > 0
          ? this.currentSlideID--
          : (this.currentSlideID = this.slides.length - 1);
        this.effect = "prev";
        this.clickable = false;
        setTimeout(this.clickswithcer, 700);
      }
    },
    next: function () {
      if (this.clickable) {
        this.currentSlideID < this.slides.length - 1
          ? this.currentSlideID++
          : (this.currentSlideID = 0);
        this.effect = "next";
        this.clickable = false;
        setTimeout(this.clickswithcer, 700);
      }
    },
    switchTo(number) {
      if (this.clickable) {
        if (this.currentSlideID < number) {
          this.effect = "next";
        } else {
          this.effect = "prev";
        }
        this.currentSlideID = number;
        this.clickable = false;
        setTimeout(this.clickswithcer, 700);
      }
    },
    clickswithcer: function () {
      this.clickable = true;
    },
  },
  data() {
    return {
      slides: [
        "/img/slider/skybox/SkyboxSlider_1.png",
        "/img/slider/skybox/SkyboxSlider_2.png",
        "/img/slider/skybox/SkyboxSlider_3.png",
        "/img/slider/skybox/SkyboxSlider_4.png",
      ],
      currentSlideID: 0,
      effect: "",
      clickable: true,
    };
  },
  props: ["ProjectName"],
};
</script>

<style lang="scss" scoped>
.slider {
  @apply flex justify-evenly flex-col;
  @apply lg:flex-row;

  & .slider-wrapper {
    @apply relative overflow-hidden flex items-end justify-center w-80 h-40;
    @apply smlger:w-108 smlger:h-56;
    @apply smplus:w-144 smplus:h-72;
    @apply lgplus:w-240 lgplus:h-120;
    @apply xl:w-280 xl:h-140;
    border-radius: 100px;

    & .project-name {
      @apply text-5xl text-purple-700 z-40;
    }
  }
}

.sliderDots {
  @apply flex mb-3;

  & .all {
    @apply cursor-pointer rounded-full w-3 h-3 top-0 -left-0 mx-2 transition-all duration-1000;
    background-color: rgba(174, 95, 255, 0.5);
    content: " ";
    position: relative;
  }

  & .active {
    @apply cursor-pointer rounded-full w-3 h-3 top-0 -left-0 mx-2 transition-all duration-1000;
    background-color: #ae5fff;
    content: " ";
    position: relative;
  }
}

.slider_and_name {
  @apply flex flex-col items-center;

  & .project-name {
    @apply text-5xl mb-2;
    font-family: "Train One";
    color: #ae5fff;
  }

  & .github {
    @apply flex self-center w-32;
    @apply md:mt-5;
    @media (min-width: 1024px) {
       
     filter: invert(95%) sepia(0%) saturate(58%) hue-rotate(4deg) brightness(120%) contrast(100%);
      
    }
  }
}
</style>