<template>
  <div class="header" :class="{ isProject: $route.name == 'Projects' }">
    <div class="logoWrapper">
      <router-link
        to="/"
        class="logo"
        :active-class="'active'"
        >adm’s</router-link
      >
    </div>
    <div class="links" v-if="$route.name != 'Projects'">
      <a href="#about" v-smooth-scroll class="link">about me</a>
      <a href="#projects" v-smooth-scroll class="link">projects</a>
      <a href="#contact" v-smooth-scroll class="link">contact</a>
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
      <div
        class="menu"
        :class="{'menuOpened': isMobileMenuOpened}"
        @click="scrollerClicked"
      >
        <a href="#about" v-smooth-scroll class="link" v-if="$route.name != 'Projects'">about me</a>
        <a href="#projects" v-smooth-scroll class="link" v-if="$route.name != 'Projects'">projects</a>
        <a href="#contact" v-smooth-scroll class="link" v-if="$route.name != 'Projects'">contact</a>
        <router-link to="/" v-else><p class="link" @click="scrollerClicked">main page</p></router-link>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "HeaderComponent",
  methods: {
    scrollerClicked: function (event) {
      if (event.target.className == "link") {
        this.isMobileMenuOpened = false;
      }
    },
  },
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
      @apply mx-14 w-36 text-white mt-2.5 h-10 flex items-center flex-col;
      @apply lg:text-5xl lg:w-44 lg:mx-7;
      @apply lgplus:mx-14;
      font-family: "Zen Tokyo Zoo";

      &::after {
        @apply w-0 transition-all duration-1000;
        content: "";
        border-top: 2px white solid;
      }

      &:hover::after {
        width: 90%;
      }
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
      @apply z-0 text-black flex flex-col w-screen items-center h-40 justify-center text-5xl transition-all duration-1000;
      @apply md:hidden;
      transform: translateY(-10rem);
      font-family: "Zen Tokyo Zoo";
    }
  }
}

.menuOpened {
  transform: translateY(8rem) !important;
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

//For Projects Page

.isProject {
  @apply justify-center;

  & .logoWrapper{
    @apply ml-0;
    @apply md:block;

    & .logo{
      @apply flex flex-col items-center;

    &::after {
        @apply w-0 mt-0.5 transition-all duration-1000;
        content: "";
        border-top: 2px white solid;
      }

      &:hover::after {
        width: 105%;
      }
    }
    
  }
}
</style>