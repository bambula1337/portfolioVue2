<template>
  <div class="formwrapper">
    <div class="bottomcontent">
      <div class="inputs">
        <div class="email">
          <p>Email</p>
          <input type="email" placeholder="mail@example.com" />
        </div>
        <div class="name">
          <p>Name</p>
          <input type="text" placeholder="John Doe" />
        </div>
        <div class="message">
          <textarea
            name=""
            id=""
            maxlength="250"
            placeholder="Message"
          ></textarea>
        </div>
      </div>
      <div class="btnwrapper">
        <p>I will write you back usually in 3 days</p>
        <button type="submit"><p>Subscribe</p></button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "ContactComponent",
};
</script>

<style lang="scss" scoped>
.formwrapper {
  @apply flex flex-col items-center bg-no-repeat mb-36 pt-52 pb-24 -mt-36;
  @apply smplus:px-0;
  background-image: url("../../assets/img/contact/bg-left.png"),
    url("../../assets/img/contact/bg-right.png");
  background-position: left center, right center;
  background-size: 0px;
  @apply lg:bg-9.5rem;
  & input:focus {
    border: 3px solid #000000;
  }
  & textarea:focus {
    border: 3px solid #000000;
  }
  & .bottomcontent {
    @apply smplus:w-100;
    @apply lg:w-100;
    & .inputs {
      @apply items-center justify-center text-black text-sm;
      font-family: "Comfortaa";
      & .email {
        @apply flex items-center mb-2;
        & input {
          @apply rounded-full text-left pl-5 h-16 w-full transition-all duration-300 outline-none;
          @apply smplus:h-16 smplus:w-full;
          @apply lg:h-14;
          background-color: rgba(243, 243, 243, 1);
        }
        & p {
          @apply text-base mr-7;
          @apply sm:hidden;
          @apply lg:block;
        }
      }
      & .name {
        @apply flex items-center;
        & input {
          @apply rounded-full text-left pl-5 h-16 w-full transition-all duration-300 outline-none;
          @apply smplus:h-16 smplus:w-full;
          @apply lg:h-14;
          background-color: rgba(243, 243, 243, 1);
        }
        & p {
          @apply text-base;
          @apply sm:hidden;
          @apply lg:block;
          margin-right: 1.4rem;
        }
      }
      & .message {
        @apply flex;
        & textarea {
          @apply rounded-3xl text-left pl-5 pt-2 pr-2 h-28 w-full mt-2 align-text-top transition-all duration-300 outline-none;
          background-color: rgba(243, 243, 243, 1);
          resize: none;
        }
        & textarea::-webkit-scrollbar {
          width: 0.6vw;
        }

        /* Track */
        & textarea::-webkit-scrollbar-track {
          @apply mt-5 -ml-4 mb-5;
          background-color: rgba(243, 243, 243, 1);
          border-radius: 30px;
        }

        /* Handle */
        & textarea::-webkit-scrollbar-thumb {
          @apply bg-gray-200;
          border-radius: 30px;
        }

        /* Handle on hover */
        & textarea::-webkit-scrollbar-thumb:hover {
          @apply bg-gray-300;
        }
      }
    }
    & .btnwrapper {
      @apply flex pt-3 items-center justify-between flex-col;
      @apply lg:flex-row;
      & p {
        @apply text-gray-400 text-lg;
        @apply smplus:text-lg;
        @apply lg:text-xs;
        font-family: "Comfortaa";
      }
      & button {
        @apply text-gray-50 bg-gradient-to-r from-gray-900 to-gray-500 rounded-full h-14 w-48 mt-4;
        @apply lg:h-11 lg:w-36 lg:text-base lg:mt-0;

        & p {
          @apply flex flex-col items-center text-blue-50 -mb-0.5;

          &::after {
            content: " ";
            @apply flex w-0 h-0 bg-gray-400 transition-all duration-700;
            border: 0px rgba(156, 163, 175, var(--tw-bg-opacity)) solid;
            font-family: "Comfortaa";
          }
        }
        &:hover {
          p {
            @apply -mb-0.5;
            &::after {
              content: " ";
              @apply flex;
              width: 50%;
              border: 0.5px rgba(156, 163, 175, var(--tw-bg-opacity)) solid;
            }
          }
        }
      }
    }
  }
}
</style>