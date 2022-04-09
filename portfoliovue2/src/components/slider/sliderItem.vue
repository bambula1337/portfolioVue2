<template>
  <transition :name="effect">
    <div class="sliderItem" v-show="currentSlideID === index">
      <img class="bgImg" :src="urlStartingFromAssets(slideImgSrc)" alt="" />
    </div>
  </transition>
</template>

<script>
export default {
  name: "SliderItemComponent",
  props: ["slideImgSrc", "currentSlideID", "index", "effect"],
  methods: {
    urlStartingFromAssets: function(url){
      return require(`@/assets${url}`);
    }
  }
};
</script>

<style lang="scss">
.sliderItem {
  @apply absolute top-0 left-0 right-0 bottom-0;

}


///PrevAnimations
.prev-enter-active {
  animation: prevInAnimation 0.8s ease-in-out;
}

.prev-leave-active {
  animation: prevOutAnimation 0.8s ease-in-out;
}

@keyframes prevInAnimation {
  from {
    transform: translateX(-100%);
  }
  to {
    transform: translateX(0);
  }
}

@keyframes prevOutAnimation {
  from {
    transform: translateX(0);
  }
  to {
    transform: translateX(100%);
  }
}


///NextAnimations
.next-enter-active {
  animation: nextInAnimation 0.8s ease-in-out;
}

.next-leave-active {
  animation: nextOutAnimation 0.8s ease-in-out;
}

@keyframes nextInAnimation {
  from {
    transform: translateX(100%);
  }
  to {
    transform: translateX(0);
  }
}

@keyframes nextOutAnimation {
  from {
    transform: translateX(0);
  }
  to {
    transform: translateX(-100%);
  }
}

</style>