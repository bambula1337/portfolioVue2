<template>
  <div class="infoComponentWrapper">
    <div class="left">
      <img class="leftImage" src="@/assets/img/info/leftimage.png" alt="" />
    </div>
    <hr class="line" />
    <hr class="mobileline" />
    <div class="right">
      <p class="infoText">
        My name is Oleg and I am front-end developer, I am 15 years old I live
        in Ukraine and streaming coding streams where you can see how I am
        creating my non-commercial projects. Despite my age now I am learning
        <span class="text-projectvue vue">Vue js</span>, also this site has been
        made with using <span class="text-projectvue">Vue js</span>,
        <span class="text-projecttailwind">Tailwind css</span>, HTML,
        <span class="text-projectjs">JS</span>,
        <span class="text-projectsccs">Sccs</span> and
        <span class="text-projectgit">git</span> as SCV. In my spare time I like
        to play games like computer games or sport games like tennis. About
        lagnuages, I can speak: English, Ukranian, Russian. Anyways you can
        contact with me and ask whatever you want to ask.
      </p>
    </div>
  </div>
</template>

<script>
export default {
  name: "InfoComponent",
};
</script>

<style lang="scss" scoped>
.infoComponentWrapper {
  background: url("../../assets/img/info/bg-left.png"),
    url("../../assets/img/info/bg-right.png");
  background-position: left center, right center;
  background-repeat: no-repeat;
  background-size: 0px;
  @apply flex justify-evenly flex-col-reverse my-7 h-120;
  @apply lg:bg-info-section-bg lg:flex-row;
  & .left {
    @apply flex self-center;
    @apply smlger:ml-2;
    @apply lg:m-0;
    & .leftImage {
      @apply rounded-3xl;
      @apply smlger:w-98 w-64;
    }
  }
  & .line {
    @apply w-1 rounded-full bg-black self-center hidden;
    @apply lgplus:flex;
    height: 28rem;
  }
  & .mobileline {
    @apply w-52 h-3 rounded-full bg-black flex self-center mb-7 mt-2;
    @apply smlger:w-80;
    @apply lg:hidden;
    border: 1px black solid;
  }
  & .right {
    @apply flex self-center mt-100 ml-0 mb-5 justify-center;
    @apply smlger:ml-5;
    @apply lg:ml-0 lg:mt-0 lg:mb-0;
    & .infoText {
      width: 75%;
      max-width: 22rem;
      @apply text-base tracking-wide;
      @apply smlger:text-xl smlger:w-96 smlger:max-w-none;
      @apply lg:w-100;
      font-family: "Ubuntu";
    }
  }
}
</style>