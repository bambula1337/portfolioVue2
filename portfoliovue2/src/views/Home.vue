<template>
  <div class="home">
    <InfoMain/>
  </div>
</template>

<script>
import InfoMain from '@/components/info/infoMain.vue';

// @ is an alias to /src
export default {
  name: "Home",
  components: {
    InfoMain,
  }
};
</script>

<style lang="scss" scoped>
.home{
}
</style>