<template>
  <div class="footer">
    <hr class="line" />
    <p class="text">Copyright © 2022 - 2022 - adm’s - Portfolio Site</p>
  </div>
</template>

<script>
export default {
  name: 'FooterComponent'
};
</script>

<style lang="scss" scoped>
.footer {
  background: url('../assets/img/footer/bg.png');
  background-position: 50% bottom;
  background-size: 60rem;
  @apply bg-no-repeat h-88 flex flex-col items-center justify-end;
  @apply lg:bg-100rem;
  @apply xl:bg-120rem xl:h-98;

  .line {
    @apply rounded-full h-0 mb-3;
    width: 70%;
    color: rgba(99, 99, 99, 1);
    border: 1px rgba(99, 99, 99, 1) solid;
  }
  .text {
    @apply mb-2 text-sm text-center;
    @apply smlger:text-base;
    color: rgba(138, 138, 138, 1);
    font-family: 'Comfortaa';
  }
}
</style>