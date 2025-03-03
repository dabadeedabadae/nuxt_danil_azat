<template>
  <header class="flex flex-row w-full relative bg-green-400 border-b-2 border-gray-400 max-sm:justify-between max-sm:z-10 max-sm:relative">
    <div class="basis-1/4 flex items-center justify-start px-8 min-w-40 max-sm:basis-auto">
      <img src="assets/images/logo.jpg" class="w-16 h-16 bg-transparent" alt="Arizona Logo">
    </div>
    <div class="basis-1/4 max-sm:hidden"></div>

    <nav
      :class="{
        'basis-1/2 flex flex-row items-center justify-end px-8 gap-4': !burger,
        'max-sm:flex max-sm:flex-col max-sm:items-center max-sm:w-full max-sm:absolute max-sm:top-full max-sm:left-0 max-sm:bg-white max-sm:z-20': burger,
        'max-sm:hidden': !burger
      }">
      <NuxtLink to="/" class="my-auto p-2 hover:bg-gray-500 hover:text-white max-sm:w-full max-sm:border-b-2 max-sm:border-black max-sm:text-center">Home</NuxtLink>
      <div class="relative my-auto p-2 hover:bg-gray-500 hover:text-white max-sm:w-full max-sm:text-center max-sm:px-0 max-sm:pb-0" @click="switch_submenu">
        Labs
        <div class="absolute top-full left-0 flex flex-col bg-white text-black w-56 text-center max-sm:relative max-sm:w-full max-sm:bg-red-100" v-show="submenu">
          <NuxtLink to="/lab3" class="my-auto p-2 border-b-2 border-black hover:bg-gray-500 hover:text-white max-sm:w-full max-sm:border-t-2 max-sm:text-center">Lab3</NuxtLink>
          <NuxtLink to="/lab4" class="my-auto p-2 border-b-2 border-black hover:bg-gray-500 hover:text-white max-sm:w-full max-sm:text-center">Lab4</NuxtLink>
          <NuxtLink to="/lab5" class="my-auto p-2 border-b-2 border-black hover:bg-gray-500 hover:text-white max-sm:w-full max-sm:text-center">Lab5</NuxtLink>
          <NuxtLink to="/lab6" class="my-auto p-2 border-b-2 border-black hover:bg-gray-500 hover:text-white max-sm:w-full max-sm:text-center">Lab6</NuxtLink>
        </div>
      </div>
      <NuxtLink to="/login" class="my-auto p-2 hover:bg-gray-500 hover:text-white max-sm:w-full max-sm:text-center">Login</NuxtLink>
      <NuxtLink to="/logout" class="my-auto p-2 hover:bg-gray-500 hover:text-white max-sm:w-full max-sm:text-center">Logout</NuxtLink>
    </nav>

    <div @click="switch_burger" class="max-sm:flex max-sm:flex-col max-sm:mr-8 max-sm:justify-between max-sm:items-center max-sm:w-8 max-sm:h-6 max-sm:mt-5">
      <span :class="{'h-[3px] w-full bg-blue-950 transition-transform': true, 'rotate-45 relative top-[9px]': burger}"></span>
      <span :class="{'h-[3px] w-full bg-blue-950 transition-opacity': true, 'opacity-0': burger}"></span>
      <span :class="{'h-[3px] w-full bg-blue-950 transition-transform': true, 'rotate-[-45deg] relative bottom-3': burger}"></span>
    </div>
  </header>

  <main class="p-5 flex bg-green-100 min-h-screen">
    <slot />
  </main>

  <footer class="flex flex-row w-full bg-green-400 border-t-2 border-gray-400 items-center justify-center px-4 py-2 gap-4">
    <a href="https://www.youtube.com/"><img src="assets/images/icons8-youtube.svg" class="w-16 h-16" alt="YouTube"></a>
    <a href="https://github.com/"><img src="assets/images/icons8-github.svg" class="w-16 h-16" alt="GitHub"></a>
    <a href="https://www.facebook.com/"><img src="assets/images/icons8-facebook.svg" class="w-16 h-16 bg-transparent" alt="Facebook"></a>
  </footer>
</template>

<script setup lang="ts">
import { useHead } from '#app'
import { ref } from 'vue'

useHead({
  script: [
    {
      async: true,
      src: 'https://www.googletagmanager.com/gtag/js?id=G-Z2TJJWNVKV',
    },
    {
      innerHTML: `
        window.dataLayer = window.dataLayer || [];
        function gtag(){ dataLayer.push(arguments); }
        gtag('js', new Date());
        gtag('config', 'G-Z2TJJWNVKV');
      `,
      type: 'text/javascript',
    },
  ],
  __dangerouslyDisableSanitizers: ['script'],
})

const burger = ref(false)
const submenu = ref(false)
const switch_burger = () => { burger.value = !burger.value }
const switch_submenu = () => { submenu.value = !submenu.value }
</script>
