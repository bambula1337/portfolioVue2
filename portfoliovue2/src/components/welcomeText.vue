<template>
  <div class="welcome">
    <div class="top">
      <div class="maintext">{{ main }}</div>
    </div>
    <div class="bot">
      <div class="subtext">{{ sub }}</div>
    </div>
  </div>
</template>

<script>
export default {
  name: "WelcomeTextComponent",
  props: ["main", "sub"],
};
</script>

<style lang="scss" scoped>
.welcome{
  @apply flex flex-col items-center;
  font-family: 'Train One';
  & .top{
    & .maintext{
      @apply text-5xl;
      @apply smlger:text-7xl;
    }
  }
  & .bot{
    .subtext{
      @apply text-xl text-projectgrey;
    }
  }
}
</style>