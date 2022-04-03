<template>
  <div class="slider-controller">
    <div class="text">
      <p>{{ currentslidenumber }} / {{ totalslides }}</p>
    </div>
    <div class="buttons">
      <div class="prev" @click="$emit('prev')">
        <p>&lt;</p>
      </div>
      <div class="next" @click="$emit('next')">
        <p>&gt;</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "SliderControllerComponent",
  emits: ["prev", "next"],
  props: ["currentslidenumber", "totalslides"],
};
</script>

<style lang="scss" scoped>
.slider-controller {
  @apply text-5xl flex flex-col justify-around items-center -mb-20;
  font-family: "Train One";

  & .buttons {
    @apply flex -mt-36 text-white;

    user-select: none; /* supported by Chrome and Opera */
    -webkit-user-select: none; /* Safari */
    -khtml-user-select: none; /* Konqueror HTML */
    -moz-user-select: none; /* Firefox */
    -ms-user-select: none; /* Internet Explorer/Edge */

    & .prev {
      @apply cursor-pointer transition-all duration-700;

      
    }

    & .next {
      @apply ml-14 cursor-pointer transition-all duration-700;

      
    }
  }
}
</style>