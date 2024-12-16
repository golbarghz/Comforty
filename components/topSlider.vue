<template>
  <div class="px-28">
    <div class="relative underlayer bg-light-gray">
      <div class="circlelayer absolute rounded-full"></div>
      <div>
        <UCarousel v-slot="{ item }" :items="items"
                   :ui="{ item: 'basis-full',
                    indicators: {
                      wrapper: 'relative bottom-24',
                      active: 'bg-dark-blue',
                      inactive: 'bg-gray-300'}}"
                   :prev-button="{
                      color: 'white',
                      icon: 'i-heroicons-arrow-left-20-solid',
                      class: 'start-20 arrowIcon ring-0 p-3'}"
                   :next-button="{
                      color: 'white',
                      icon: 'i-heroicons-arrow-right-20-solid',
                      class: 'end-20 arrowIcon ring-0 p-3'}"
                   arrows
                   class="rounded-lg overflow-hidden"
                   indicators>
          <div class="flex justify-between items-center py-20 px-48 w-full">
            <div>
              <span class="text-dark-blue text-sm font-light block tracking-widest">WELCOME TO CHAIRY</span>
              <span class="text-dark-blue font-bold mt-4 block"
                    style="font-size: 68px;width: 600px!important;line-height: 74px">{{ item.text }}</span>
              <button
                  class="flex justify-between items-center py-3.5 px-6 gap-6 rounded-lg bg-secondary text-white mt-10">
                Shop Now
                <img src="../assets/svg/Right.svg">
              </button>
            </div>
            <div class="relative">
              <img :src="getImageAbsolutePath(item.img)" draggable="false">
              <div class="bg-white rounded-full flex flex-col justify-center items-center absolute -right-12 -top-3"
                   style="width: 140px;height: 124px">
                <span class="text-4xl font-bold" style="color: #F05C52">54%</span>
                <span class="text-sm text-dark-blue">Discount</span>
              </div>
            </div>

          </div>
        </UCarousel>
      </div>
      <div class="w-full absolute -bottom-28 px-48 pb-10">
        <div class="rounded-xl bg-white px-16 py-12 flex justify-between items-center w-full low-shadow">
          <div v-for="item in options" class="flex gap-4 items-center">
            <img :src="getSvgAbsolutePath(item.icon)"/>
            <div class="flex flex-col items-start gap-1">
              <span class="text-lg text-dark-blue">{{ item.label }}</span>
              <span class="text-gray-400">{{ item.text }}</span>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script setup lang="ts">
import {ref} from 'vue'

const items = ref([
  {
    text: 'Best Furniture\n' +
        'Collection for your\n' +
        'interior.',
    img: 'ProductImage.png'
  },
  {
    text: 'Best Furniture\n' +
        'Collection for your\n' +
        'interior.',
    img: 'ProductImage.png'
  }
])
const options = ref([
  {
    label: 'Discount',
    text: 'Every week new sales',
    icon: 'box.svg'
  },
  {
    label: 'Free Delivery',
    text: '100% Free for all orders',
    icon: 'delivery-truck.svg'
  },
  {
    label: 'Great Support 24/7',
    text: 'We care your experiences',
    icon: '24-hours.svg'
  },
  {
    label: 'Secure Payment',
    text: '100% Secure Payment Method',
    icon: 'shield.svg'
  },

])
const glob: Record<string, any> = import.meta.glob("~/assets/img/*", {
  eager: true,
});
const glob2: Record<string, any> = import.meta.glob("~/assets/svg/*", {
  eager: true,
});

const getImageAbsolutePath = (imageName: string): string => {
  return glob[`/assets/img/${imageName}`]["default"];
};
const getSvgAbsolutePath = (svgName: string): string => {
  return glob2[`/assets/svg/${svgName}`]["default"];
};
</script>


<style>
.underlayer {
  height: 850px;
  border-bottom-right-radius: 48px;
  border-bottom-left-radius: 48px;
}

.circlelayer {
  width: 747px;
  height: 747px;
  top: -196px;
  right: 125px;
  background-color: #E1E3E5;
}

.arrowIcon span {
  color: #007580 !important;
  width: 16px;
  height: 16px;
}

.low-shadow {
  box-shadow: 0px 24px 100px 0px rgba(22, 25, 50, 0.07);

}
</style>
