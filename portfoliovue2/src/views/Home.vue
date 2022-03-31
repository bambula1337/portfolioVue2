<template>
  <div class="home">
    <InfoMain/>
    <ContactMain/>
  </div>
</template>

<script>
import InfoMain from '@/components/info/infoMain.vue';
import ContactMain from '@/components/contact/contactmain.vue';

// @ is an alias to /src
export default {
  name: "Home",
  components: {
    InfoMain,
    ContactMain,
  }
};
</script>

<style lang="scss" scoped>
.home{
}
</style>