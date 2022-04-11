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
          @mousedown.prevent="start"
          @mousemove.prevent="move"
          @mouseup="end"
          @touchstart="start($event.touches[0])"
          @touchmove="move($event.touches[0])"
          @touchend="end"
        >
          <SliderItem
            v-for="(slide, index) in slides"
            :key="index"
            :slideImgSrc="slide"
            :currentSlideID="currentSlideID"
            :index="index"
            :effect="animation.name"
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
      if (this.isClickAble) {
        this.currentSlideID > 0
          ? this.currentSlideID--
          : (this.currentSlideID = this.slides.length - 1);
        this.animation.name = "prev";
        this.afterChangingSlide();
      }
    },
    next: function () {
      if (this.isClickAble) {
        this.currentSlideID < this.slides.length - 1
          ? this.currentSlideID++
          : (this.currentSlideID = 0);
        this.animation.name = "next";
        this.afterChangingSlide();
      }
    },
    switchTo(number) {
      if (this.isClickAble) {
        if (this.currentSlideID < number) {
          this.animation.name = "next";
        } else {
          this.animation.name = "prev";
        }
        this.currentSlideID = number;
        this.afterChangingSlide();
      }
    },
    isClickAbleSwitcher: function (value) {
      this.isClickAble = value;
    },
    intervalClear: function () {
      clearInterval(this.interval.parent);
    },
    intervalSet: function () {
      if(this.interval.isEnable){
        this.interval.parent = setTimeout(this.next, this.interval.time);
      }
    },
    start: function (currentTouch) {
      this.touch.start = currentTouch.clientX;
      this.touch.end += 1;
    },
    move: function (currentTouch) {
      this.touch.end = currentTouch.clientX;
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
    afterChangingSlide: function () {
      this.isClickAbleSwitcher(false);
      setTimeout(this.isClickAbleSwitcher, this.animation.time, true);
      clearInterval(this.interval.parent);
      this.intervalSet();
    },
  },
  created() {
    this.intervalSet();
  },
  props: ["ProjectName", "Slides", "IntervalAbility", "IntervalTime"],
  data() {
    return {
      slides: [
        ...this.Slides
      ],
      currentSlideID: 0,
      isClickAble: true,
      interval: {
        isEnable: this.IntervalAbility,
        parent: null,
        time: this.IntervalTime,
      },
      touch: {
        start: 0,
        end: 0,
      },
      animation: {
        name: '',
        time: 700,
      }
    };
  },
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