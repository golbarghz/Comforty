<template>
  <div class="w-full border-y border-gray-200 px-80 py-20">
    <div class="grid grid-cols-4 xl:grid-cols-6 w-full">
      <div class="col-span-2">
        <div class="flex items-center text-dark-blue text-xl font-medium gap-3">
          <img src="~/assets/img/LogoIcon.png">
          Comforty
        </div>
        <p class="text-dark-blue opacity-60 font-normal my-8">
          Vivamus tristique odio sit amet velit semper,<br/> eu posuere turpis interdum.<br/>
          Cras egestas purus
        </p>
        <div class="flex gap-3 items-center">
          <img src="~/assets/svg/facebook.svg">
          <img src="~/assets/svg/twitter.svg">
          <img src="~/assets/svg/instagram.svg">
          <img src="~/assets/svg/pinterest.svg">
          <img src="~/assets/svg/youTube.svg">
        </div>
      </div>
      <div class="flex flex-col gap-2.5 col-span-1">
        <p class="text-sm text-gray-400 font-medium pb-2">
          CATEGORY
        </p>
        <p class="text-dark-blue hover:text-secondary hover:underline hover:underline-offset-4 cursor-pointer "
           v-for="item in category">{{ item }}</p>
      </div>
      <div class="flex flex-col gap-2.5 col-span-1">
        <p class="text-sm text-gray-400 font-medium pb-2">
          SUPPORT
        </p>
        <p class="text-dark-blue hover:text-secondary hover:underline hover:underline-offset-4 cursor-pointer "
           v-for="item in support">{{ item }}</p>
      </div>
      <div class="col-span-2">
        <p class="text-sm text-gray-400 font-medium pb-5">
          Newsletter
        </p>
        <div class="flex items-center gap-3">
          <input v-model="email"
                 placeholder="Your email"
                 class="p-3 rounded-lg border border-gray-300" style="width: 285px"/>
          <button class="text-white font-semibold py-3 px-5 rounded-lg bg-secondary">Subscribe</button>

        </div>
        <p class="text-dark-blue opacity-60 font-normal mt-5" style="font-size: 15px">
          Lorem ipsum dolor sit amet, consectetur adipiscing elit.<br/> Nullam tincidunt erat enim.
        </p>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import {ref} from 'vue'

const category = ref(['Sofa', 'Armchair', 'Wing Chair', 'Desk Chair', 'wooden Chair', 'Park Bench'])
const support = ref(['Help & Support', 'Tearms & Conditions', ' Privacy Policy', 'Help'])
const email = ref()
</script>