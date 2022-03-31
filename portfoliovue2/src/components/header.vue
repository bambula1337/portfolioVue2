<template>
  <div class="header">
    <div class="logoWrapper">
      <router-link to="/" class="logo" :active-class="'active'"
        >adm’s</router-link
      >
    </div>
    <div class="links">
      <router-link to="/contact" class="link" :active-class="'active'"
        >about me</router-link
      >
      <router-link to="/contact" class="link" :active-class="'active'"
        >projects</router-link
      >
      <router-link to="/contact" class="link" :active-class="'active'"
        >contact</router-link
      >
    </div>
    <div class="mobilemenu">
      <div class="opener">
        <input type="checkbox" class="checker" v-model="isMobileMenuOpened" />
        <span
          :class="[
            isMobileMenuOpened ? 'openerContentOpened' : 'openerContent',
          ]"
        ></span>
      </div>
      <div :class="[isMobileMenuOpened ? 'menuOpened' : 'menu']">
        <router-link to="/contact" class="link" :active-class="'active'"
          >about me</router-link
        >
        <router-link to="/contact" class="link" :active-class="'active'"
          >projects</router-link
        >
        <router-link to="/contact" class="link" :active-class="'active'"
          >contact</router-link
        >
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "HeaderComponent",
  data() {
    return {
      isMobileMenuOpened: false,
    };
  },
};
</script>

<style lang="scss" scoped>
.header {
  background: url("../assets/img/header/background.png");
  background-size: 50rem;
  background-position: 90% top;
  @apply flex justify-around bg-no-repeat overflow-hidden h-72;
  @apply md:bg-70rem;
  @apply lg:bg-80rem lgplus:bg-90rem xl:bg-120rem lgplus:bg-headerbg;
  & .logoWrapper {
    @apply hidden mt-2 ml-7;
    @apply lg:block;
    & .logo {
      @apply text-5xl text-white;
      font-family: "Train One";
    }
  }
  & .links {
    margin-right: 10%;
    margin-left: 10%;
    @apply hidden;
    @apply md:flex;
    @apply lg:mx-0;
    & .link {
      font-size: 2.5rem;
      @apply mx-14 w-36 text-white mt-2.5 h-10;
      @apply lg:text-5xl lg:w-44 lg:mx-7;
      @apply lgplus:mx-14;
      font-family: "Zen Tokyo Zoo";
    }
  }
  & .mobilemenu {
    & .opener {
      @apply md:hidden;
      & .checker {
        @apply absolute -ml-5 w-10 h-10 z-70 opacity-0;
        top: 7.5%;
        left: 50%;
      }
      & .openerContent {
        @apply rounded-full -ml-5 z-20;
        content: "";
        position: absolute;
        top: calc(10% - 1px);
        left: 50%;
        width: 2.5rem;
        border-bottom: 4px solid rgb(255, 255, 255);
        transition: all 0.6s cubic-bezier(0.215, 0.61, 0.355, 1);

        &::after,
        &::before {
          @apply rounded-full;
          content: "";
          position: absolute;
          top: 50%;
          left: 0%;
          width: 2.5rem;
          border-bottom: 4px solid rgb(255, 255, 255);
          transition: transform 0.6s cubic-bezier(0.215, 0.61, 0.355, 1);
        }

        &::after {
          transform: translateY(-12px);
        }

        &::before {
          transform: translateY(12px);
        }
      }
    }
    & .menu {
      @apply z-0 text-black flex flex-col w-screen items-center h-40 justify-center -mt-40 text-5xl transition-all duration-1000;
      @apply md:hidden;
      font-family: "Zen Tokyo Zoo";
    }
  }
}

.menuOpened {
  @apply z-0 text-black flex flex-col w-screen items-center h-40 justify-center mt-32 text-5xl  transition-all duration-1000;
  @apply md:hidden;
  font-family: "Zen Tokyo Zoo";
}

.openerContentOpened {
  @apply rounded-full -ml-5;
  content: "";
  position: absolute;
  top: calc(10% - 1px);
  left: 50%;
  width: 0rem;
  border-bottom: 4px solid rgb(255, 255, 255);
  transition: all 0.6s cubic-bezier(0.215, 0.61, 0.355, 1);

  &::after,
  &::before {
    @apply rounded-full;
    content: "";
    position: absolute;
    top: 50%;
    left: 0%;
    width: 2.5rem;
    border-bottom: 4px solid rgb(255, 255, 255);
    transition: transform 0.6s cubic-bezier(0.215, 0.61, 0.355, 1);
  }

  &::after {
    transform: translateY(-12px);
    transform: rotate(45deg);
  }

  &::before {
    transform: translateY(12px);
    transform: rotate(-45deg);
  }
}
</style>