<template>
  <div class="contactmain" id="contact">
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
  @apply mt-48 -mb-52;
  @apply lg:mt-36 lg:-mb-10;
}
</style>