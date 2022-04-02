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
        "@/assets/img/slider/skybox/skybox_1.png",
        "https://picsum.photos/id/232/1920/1080",
        "https://picsum.photos/id/233/1920/1080",
        "https://picsum.photos/id/234/1920/1080",
        "https://picsum.photos/id/235/1920/1080",
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
  @apply flex justify-evenly -ml-10;

  & .slider-wrapper {
    @apply relative overflow-hidden flex items-end justify-center;
    border-radius: 100px;
    width: 1200px;
    height: 500px;

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

.slider_and_name{
  @apply flex flex-col items-center;

  & .project-name{
    @apply text-5xl mb-2;
    font-family: 'Train One';
    color: #AE5FFF;
  }
}
</style>