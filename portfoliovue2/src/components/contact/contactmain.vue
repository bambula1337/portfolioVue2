<template>
  <div class="contactmain">
    <WelcomeText :main="WelcomeTextProps.main" :sub="WelcomeTextProps.sub"/>
    <ContactComponent/>
  </div>
</template>

<script>
import WelcomeText from '@/components/welcomeText.vue';
import ContactComponent from '@/components/contact/contact.vue'

export default {
  name: 'ContactMain',
  components: {
    WelcomeText,
    ContactComponent,
  },
  data(){
    return{
      WelcomeTextProps: {
        main: 'Drop me a line',
        sub: 'How to contact with me',
      }
    }
  }
}
</script>

<style lang="scss" scoped>
.contactmain{
  @apply mt-88;
  @apply smlger:mt-108;
  @apply lg:mt-52;
}
</style>