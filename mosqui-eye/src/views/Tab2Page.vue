<template>
  <ion-content class="overflow-hidden pl-16 bg-white rounded-3xl max-md:pl-5">
    <section class="flex gap-5 max-md:flex-col">
      <div class="flex flex-col w-[42%] max-md:ml-0 max-md:w-full">
        <form @submit.prevent="handleSubmit" class="flex flex-col self-stretch my-auto w-full text-xs max-md:mt-10">
          <h1 class="self-center text-3xl text-black uppercase">Login</h1>
          <p class="mr-6 ml-6 text-base text-neutral-600 max-md:mx-2.5">
            Welcome to Moquieye Web Application
          </p>
          <div class="relative">
            <label for="username" class="sr-only">Username</label>
            <div class="flex gap-1.5 px-5 py-3.5 mt-3.5 whitespace-nowrap rounded-2xl bg-violet-100 bg-opacity-80 text-zinc-900">
              <ion-icon name="person" class="shrink-0 w-6"></ion-icon>
              <ion-input 
                id="username"
                v-model="username"
                type="text"
                class="flex-auto my-auto w-[293px] bg-transparent border-none focus:outline-none"
                placeholder="Username"
                required
              ></ion-input>
            </div>
          </div>
          <div class="relative">
            <label for="password" class="sr-only">Password</label>
            <div class="flex gap-1.5 px-5 py-3.5 mt-5 whitespace-nowrap rounded-2xl bg-violet-100 bg-opacity-80 text-zinc-900">
              <ion-icon name="lock-closed" class="shrink-0 w-6"></ion-icon>
              <ion-input 
                id="password"
                v-model="password"
                type="password"
                class="flex-auto my-auto w-[293px] bg-transparent border-none focus:outline-none"
                placeholder="Password"
                required
              ></ion-input>
            </div>
          </div>
          <ion-button 
            type="submit"
            class="self-center px-8 py-4 mt-6 max-w-full font-bold text-white rounded-2xl shadow-[0px_8px_21px_rgba(0,0,0,0.16)] w-[124px] max-md:px-5 bg-blue-600 hover:bg-blue-700 focus:outline-none focus:ring-2 focus:ring-blue-500 focus:ring-offset-2"
          >
            Login Now
          </ion-button>
          <ion-label 
            @click.prevent="handleForgotPassword"
            class="self-center mt-5 font-semibold text-center text-blue-600 hover:text-blue-700 focus:outline-none focus:underline"
          >
            Forgot password?
          </ion-label>
        </form>
      </div>
      <div class="flex flex-col ml-5 w-[58%] max-md:ml-0 max-md:w-full">
        <div class="flex relative flex-col grow min-h-[575px] max-md:mt-10 max-md:max-w-full">
          <img loading="lazy" src="https://cdn.builder.io/api/v1/image/assets/TEMP/a204c366aadf3cc4b80ff8feeeb08318b2248cf7990441372c3c40430a14ab7e?placeholderIfAbsent=true&apiKey=de1f00a26d574dd4946df02ba77aa674" alt="Login background" class="object-cover absolute inset-0 size-full" />
          <img loading="lazy" src="https://cdn.builder.io/api/v1/image/assets/TEMP/e8dcf3fdbe2995d2a77b159f23887cdb96d5e4f39b37659f16b0cc9e5cb2b9f2?placeholderIfAbsent=true&apiKey=de1f00a26d574dd4946df02ba77aa674" alt="Login illustration" class="object-contain w-full aspect-[0.89] max-md:max-w-full" />
        </div>
      </div>
    </section>
  </ion-content>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue';

export default defineComponent({
  name: 'LoginPage',
  setup() {
    const username = ref('');
    const password = ref('');

    const handleSubmit = () => {
      // Handle login submission
      console.log('Login submitted', { username: username.value, password: password.value });
    };

    const handleForgotPassword = () => {
      // Handle forgot password
      console.log('Forgot password clicked');
    };

    return {
      username,
      password,
      handleSubmit,
      handleForgotPassword,
    };
  },
});
</script>

<style scoped>
.builder-component {
  max-width: none !important;
}
</style>
