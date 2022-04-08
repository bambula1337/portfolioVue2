<template>
  <div class="slider">
    <div class="slider_and_name">
      <p class="project-name">{{ ProjectName }}</p>
      <div
        class="slider-wrapper"
        @mouseover="intervalClear"
        @mouseleave="intervalSet"
      >
        <div
          class="item-wrapper"
          @mousedown="start"
          @mousemove="move"
          @mouseup="end"
        >
          <SliderItem
            v-for="(slide, index) in slides"
            :key="index"
            :slideImgSrc="slide"
            :currentSlideID="currentSlideID"
            :index="index"
            :effect="effect"
          />
        </div>
        <div class="sliderDots">
          <p
            v-for="(dot, index) in slides"
            :key="index"
            @click="switchTo(index)"
            :class="[currentSlideID == index ? 'active' : 'all']"
          ></p>
        </div>
      </div>
      <a href="https://github.com/bambula1337/CopyProIdea" class="github"
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
        clearInterval(this.interval);
        this.interval = setTimeout(this.next, 5000);
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
        clearInterval(this.interval);
        this.interval = setTimeout(this.next, 5000);
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
        clearInterval(this.interval);
        this.interval = setTimeout(this.next, 5000);
      }
    },
    clickswithcer: function () {
      this.clickable = true;
    },
    intervalClear: function () {
      clearInterval(this.interval);
    },
    intervalSet: function () {
      this.interval = setTimeout(this.next, 5000);
    },
    start: function (event) {
      event.preventDefault();
      this.touch.start = event.clientX;
      this.touch.end = this.touchstart + 1;
    },
    move: function (event) {
      event.preventDefault();
      this.touch.end = event.clientX;
    },
    end: function () {
      if (Math.abs(this.touch.end - this.touch.start) > 50) {
        if (this.touch.end < this.touch.start) {
          this.next();
        } else {
          this.prev();
        }
      }
    },
    touchstart: function (event) {
      event.preventDefault();
      this.touch.start = event.touches[0].clientX;
      this.touch.end = this.touchstart + 1;
    },
    touchmove: function (event) {
      event.preventDefault();
      this.touch.end = event.touches[0].clientX;
    },
    touchend: function () {
      console.log(this.touch);
      if (Math.abs(this.touch.end - this.touch.start) > 50) {
        if (this.touch.end < this.touch.start) {
          this.next();
        } else {
          this.prev();
        }
      }
    },
  },
  created() {
    this.interval = setTimeout(this.next, 5000);
  },
  mounted() {
    console.log(this.$el.querySelector(".slider-wrapper"));
    this.$el
      .querySelector(".item-wrapper")
      .addEventListener("touchstart", this.touchstart);
    this.$el
      .querySelector(".item-wrapper")
      .addEventListener("touchmove", this.touchmove);
    this.$el
      .querySelector(".item-wrapper")
      .addEventListener("touchend", this.touchend);
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
      interval: null,
      touch: {
        start: 0,
        end: 0,
      },
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
    -webkit-box-shadow: 0px 0px 10px 3px #ffffff7c;
    box-shadow: 0px 0px 10px 3px #ffffff7c;
  }

  & .active {
    @apply cursor-pointer rounded-full w-3 h-3 top-0 -left-0 mx-2 transition-all duration-1000;
    background-color: #ae5fff;
    content: " ";
    position: relative;
    -webkit-box-shadow: 0px 0px 10px 3px #ffffff;
    box-shadow: 0px 0px 10px 3px #ffffff;
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
      filter: invert(95%) sepia(0%) saturate(58%) hue-rotate(4deg)
        brightness(120%) contrast(100%);
    }
  }
}
</style>