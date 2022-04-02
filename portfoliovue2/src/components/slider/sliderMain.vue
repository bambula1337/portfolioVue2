<template>
  <div class="sliderMain">
    <Slider :ProjectName="ProjectName"/>
  </div>
</template>

<script>
import Slider from '@/components/slider/slider.vue';

export default {
  name: 'SliderMain',
  components: {
    Slider,
  },
  data(){
    return{
      ProjectName: 'SKYBOX',
    }
  }
}
</script>

<style lang="scss" scoped>

</style>