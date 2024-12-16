<template>
  <div class="mb-20">
    <top-slider/>
    <div class="px-80 w-full mt-20">
      <div class="flex w-full flex justify-between items-center">
        <div v-for="item in brands" :key="item">
          <img :src="getImageAbsolutePath(item)"/>
        </div>
      </div>
      <div class="mt-20">
        <span class="text-2xl font-semibold text-dark-blue">Featured Products</span>
        <div>
          <UCarousel v-slot="{ item }" :items="allProducts"
                     :ui="{ item: 'basis-1/2 md:basis-1/3 lg:basis-1/4',
                     container:'gap-6',
                    }"
                     :prev-button="{
                      color: 'white',
                      icon: 'i-heroicons-arrow-left-20-solid',
                      class: 'start-0 arrowIcon ring-0 p-3'}"
                     :next-button="{
                      color: 'white',
                      icon: 'i-heroicons-arrow-right-20-solid',
                      class: 'end-0 arrowIcon ring-0 p-3'}"
                     arrows
                     class=" overflow-hidden pt-10"
          >
            <div>
              <div class="relative">
                <img :src="getImageAbsolutePath(item.src)" draggable="false">
                <span v-show="item.isNew"
                      class="bg-green-600 text-white text-xs absolute top-4 left-4 p-1 px-1.5 rounded">New</span>
                <div v-show="item.isNew" class="bg-white rounded-lg p-2.5 absolute top-4 right-4">
                  <icon-heart/>
                </div>
                <span v-show="item.onSale"
                      class="bg-orange-500 text-white text-xs absolute top-4 left-4 p-1 px-1.5 rounded">Sales</span>
              </div>
              <div class="mt-5 flex justify-between w-full items-start">
                <div>
                  <p :class="item.selected ?'text-secondary':'text-dark-blue'">Library Stool Chair</p>
                  <p class="text-lg mt-2">$20</p>
                </div>
                <button @click="item.selected = !item.selected" class="p-2.5 rounded-lg"
                        :class="item.selected ? 'bg-secondary':'bg-light-gray'">
                  <img v-if="item.selected" src="~/assets/svg/Buy-white.svg">
                  <img v-else src="~/assets/svg/Buy.svg">
                </button>
              </div>
            </div>
          </UCarousel>
        </div>
      </div>
    </div>
    <div class="mt-20">
      <span class="text-2xl font-semibold text-dark-blue px-80">Top categories</span>
      <div>
        <UCarousel v-slot="{ item }" :items="categories"
                   :ui="{ item: 'basis-1/2 md:basis-1/3 lg:basis-1/5',
                     container:'gap-6',
                    }"
                   class=" overflow-hidden pt-10">
          <div>
            <div class="relative rounded-lg">
              <img style="height: 336px;width: 336px" :src="getImageAbsolutePath(item.src)" draggable="false">
              <div class="w-full bg-black/60 absolute bottom-0 rounded-b-lg p-2.5">
                <p class="text-white text-xl">{{ item.name }}</p>
                <p class="text-white text-xs mt-1">{{ item.info }}</p>
              </div>
            </div>

          </div>
        </UCarousel>
      </div>
    </div>
    <div class="px-80 w-full mt-20 flex flex-col items-center">
      <span class="text-2xl font-semibold text-dark-blue">Our Products</span>
      <div class="flex  gap-4 mt-6">
        <p class="text-dark-blue pb-2 border-b-2 border-secondary">ALL</p>
        <p class="text-gray-400 hover:text-dark-blue  cursor-pointer " v-for="item in folders">{{ item }}</p>
      </div>
      <div class="grid grid-cols-4 gap-x-6 gap-y-10 mt-10">
        <div v-for="item in allProducts">
          <div class="relative">
            <img :src="getImageAbsolutePath(item.src)" draggable="false">
            <span v-show="item.isNew" class="bg-green-600 text-white text-xs absolute top-4 left-4 p-1 px-1.5 rounded">New</span>
            <div v-show="item.isNew" class="bg-white rounded-lg p-2.5 absolute top-4 right-4">
              <icon-heart/>
            </div>
            <span v-show="item.onSale"
                  class="bg-orange-500 text-white text-xs absolute top-4 left-4 p-1 px-1.5 rounded">Sales</span>
          </div>
          <div class="mt-5 flex justify-between w-full items-start">
            <div>
              <p :class="item.selected ?'text-secondary':'text-dark-blue'">Library Stool Chair</p>
              <p class="text-lg mt-2">$20</p>
            </div>
            <button @click="item.selected = !item.selected" class="p-2.5 rounded-lg"
                    :class="item.selected ? 'bg-secondary':'bg-light-gray'">
              <img v-if="item.selected" src="~/assets/svg/Buy-white.svg">
              <img v-else src="~/assets/svg/Buy.svg">
            </button>
          </div>
        </div>
      </div>
    </div>
    <div class="w-full bg-light-gray px-80 py-20 mt-20">
      <span class="text-2xl font-semibold text-dark-blue">What client says about us</span>
      <div>
        <UCarousel v-slot="{ item }" :items="comments"
                   :ui="{ item: 'basis-1/2',
                     container:'gap-6',
                    }"
                   class=" overflow-hidden pt-10">
          <div>
            <div class="rounded-lg p-6 bg-white flex flex-col justify-between"
                 style="height: 345px;box-shadow: 0px 8px 40px 0px rgba(39, 35, 67, 0.08);">
              <p class="text-tertiary text-lg font-normal pl-6 border-l-2 border-secondary">
                {{ item.text }}
              </p>
              <div class="flex justify-between mt-4 items-center">
                <div class="flex items-center gap-2">
                  <img :src="getImageAbsolutePath(item.img)" draggable="false">
                  <div>
                    <p class="text-dark-blue text-lg">{{ item.username }}</p>
                    <p class="text-gray-400">{{ item.job }}</p>
                  </div>
                </div>
                <img src="~/assets/svg/cm.svg">
              </div>
            </div>

          </div>
        </UCarousel>
      </div>

    </div>
    <div class="px-80">
      <div class="mt-20">
        <span class="text-2xl font-semibold text-dark-blue">Recently Added</span>
        <div>
          <UCarousel v-slot="{ item }" :items="allProducts"
                     :ui="{ item: 'basis-1/2 md:basis-1/3 lg:basis-1/4',
                     container:'gap-6',
                    }"
                     class=" overflow-hidden pt-10">
            <div>
              <div class="relative">
                <img :src="getImageAbsolutePath(item.src)" draggable="false">
                <span v-show="item.isNew"
                      class="bg-green-600 text-white text-xs absolute top-4 left-4 p-1 px-1.5 rounded">New</span>
                <div v-show="item.isNew" class="bg-white rounded-lg p-2.5 absolute top-4 right-4">
                  <icon-heart/>
                </div>
                <span v-show="item.onSale"
                      class="bg-orange-500 text-white text-xs absolute top-4 left-4 p-1 px-1.5 rounded">Sales</span>
              </div>
              <div class="mt-5 flex justify-between w-full items-start">
                <div>
                  <p :class="item.selected ?'text-secondary':'text-dark-blue'">Library Stool Chair</p>
                  <p class="text-lg mt-2">$20</p>
                </div>
                <button @click="item.selected = !item.selected" class="p-2.5 rounded-lg"
                        :class="item.selected ? 'bg-secondary':'bg-light-gray'">
                  <img v-if="item.selected" src="~/assets/svg/Buy-white.svg">
                  <img v-else src="~/assets/svg/Buy.svg">
                </button>
              </div>
            </div>
          </UCarousel>
        </div>
      </div>
    </div>
  </div>


</template>
<script setup lang="ts">

import {ref} from 'vue'

useHead({
  title: "Home",
});
const glob: Record<string, any> = import.meta.glob("~/assets/img/*", {
  eager: true,
});
const getImageAbsolutePath = (imageName: string): string => {
  return glob[`/assets/img/${imageName}`]["default"];
};
const brands = ref(['Logo.png', 'Logo(1).png', 'Logo(2).png', 'Logo(3).png', 'Logo(4).png', 'Logo(5).png', 'Logo(6).png'])
const allProducts = ref([
  {
    src: 'Image.png',
    isNew: true,
    onSale: false,
    selected: true
  },
  {
    src: 'Image(1).png',
    isNew: false,
    onSale: true,
    selected: false
  },
  {
    src: 'Image(2).png',
    isNew: false,
    onSale: false,
    selected: false
  },
  {
    src: 'Image(3).png',
    isNew: false,
    onSale: false,
    selected: false
  },
  {
    src: 'Image(4).png',
    isNew: true,
    onSale: false,
    selected: false
  },
  {
    src: 'Image(5).png',
    isNew: false,
    onSale: true,
    selected: false
  },
  {
    src: 'Image(6).png',
    isNew: false,
    onSale: false,
    selected: false
  },
  {
    src: 'Image(7).png',
    isNew: false,
    onSale: false,
    selected: false
  },
])
const categories = ref([

  {
    name: 'Sofa',
    info: '110 Products',
    src: 'Image(12).png'
  },
  {
    name: 'Wing Chair',
    info: '3,584 Products',
    src: 'Image(8).png'
  },
  {
    name: 'Wooden Chair',
    info: '157 Products',
    src: 'Image(9).png'
  },
  {
    name: 'Desk Chair',
    info: '154 Products',
    src: 'Image(10).png'
  },
  {
    name: 'Park Bench',
    info: '154 Products',
    src: 'Image(11).png'
  }
])
const folders = ref(['NEWEST', 'TRENDING', 'BEST SELLERS', 'FEATURED'])
const comments = ref([
  {
    text: '“Lorem ipsum dolor sit amet, consectetur adipiscing elit. Vivamus sit amet mi nec massa tincidunt blandit et eu sem.' +
        ' Maecenas laoreet ultrices diam dignissim posuere. Aenean ultrices dui at ipsum sagittis,' +
        ' pharetra lacinia dui faucibus. In ac bibendum ex. Aenean dolor massa, euismod sit amet suscipit et“',
    username: 'Kristin Watson',
    job: 'Fashion Designer',
    img: 'avatar2.png'
  },
  {
    text: 'Nullam sapien elit, dignissim eu viverra et, scelerisque et felis. Aliquam egestas dui elit, quis tincidunt lacus aliquam et. Duis nulla velit, dignissim ut odio ac,' +
        ' eleifend luctus leo. Ut ac imperdiet velit. Aliquam semper ex in volutpat rutrum.',
    username: 'Esther Howard',
    job: 'Fashion Designer',
    img: 'avatar1.png'
  },
  {
    text: '“Lorem ipsum dolor sit amet, consectetur adipiscing elit. Vivamus sit amet mi nec massa tincidunt blandit et eu sem.' +
        ' Maecenas laoreet ultrices diam dignissim posuere. Aenean ultrices dui at ipsum sagittis,' +
        ' pharetra lacinia dui faucibus. In ac bibendum ex. Aenean dolor massa, euismod sit amet suscipit et“',
    username: 'Kristin Watson',
    job: 'Fashion Designer',
    img: 'avatar2.png'
  }
])
</script>