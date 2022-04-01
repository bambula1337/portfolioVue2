<template>
  <div class="infoMain" id="about">
    <WelcomeText :main="WelcomeTextProps.main" :sub="WelcomeTextProps.sub"/>
    <Info/>
  </div>
</template>

<script>
import WelcomeText from '@/components/welcomeText.vue';
import Info from '@/components/info/info.vue';

export default {
  name: 'InfoMain',
  components: {
    WelcomeText,
    Info,
  },
  data(){
    return{
      WelcomeTextProps:{
        main: 'Who Am I?',
        sub: 'front-end developer',
      }
    }
  }
}
</script>

<style lang="scss" scoped>

</style>