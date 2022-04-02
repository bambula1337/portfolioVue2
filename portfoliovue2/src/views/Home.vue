<template>
  <div class="home">
    <InfoMain/>
    <ContactMain/>
    <SliderMain/>
  </div>
</template>

<script>
import InfoMain from '@/components/info/infoMain.vue';
import ContactMain from '@/components/contact/contactmain.vue';
import SliderMain from '@/components/slider/sliderMain.vue';

// @ is an alias to /src
export default {
  name: "Home",
  components: {
    InfoMain,
    ContactMain,
    SliderMain,
  }
};
</script>

<style lang="scss" scoped>
.home{
}
</style>