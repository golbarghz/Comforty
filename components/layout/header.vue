<template>
  <div>
    <div class="w-full bg-dark-blue flex justify-between px-80 h-11 items-center font-normal">
      <div class="flex items-center gap-2 text-xs text-white ">
        <img src="~/assets/svg/check.svg">
        Free shipping on all orders over $50
      </div>
      <div class="flex items-center gap-6 text-xs text-white font-normal">
        <div class="flex items-center gap-2 cursor-pointer">
          Eng
          <img src="~/assets/svg/arrowDown.svg">
        </div>
        <div class="cursor-pointer">Faqs</div>
        <div class="flex items-center gap-2 cursor-pointer">

          <img src="~/assets/svg/alert-circle.svg">
          Need Help
        </div>
      </div>
    </div>
    <div class="bg-light-gray w-full px-80 h-22 flex justify-between items-center">
      <div class="flex items-center text-dark-blue text-xl font-medium gap-3">
        <img src="~/assets/img/LogoIcon.png">
        Comforty
      </div>
      <div class="flex justify-center items-center w-1/3">
        <div class="rounded-lg bg-white flex  justify-between items-center p-3 w-full">
          <input v-model="search"
                 placeholder="Search here ..."
                 class="w-4/5 text-sm"/>
          <img src="~/assets/svg/search.svg" class="cursor-pointer"/>
        </div>
      </div>
      <div class="flex items-center gap-2">
        <div class="bg-white rounded-lg p-3 flex items-center gap-2 cursor-pointer text-xs">
          <img src="~/assets/svg/Buy.svg">
          Cart
          <span class="flex justify-center items-center rounded-full text-white"
                style="background-color: #007580;font-size: 10px;width: 20px;height: 20px">{{ buyCount }}</span>
        </div>
        <button @click="liked = !liked" class="bg-white rounded-lg p-3 ">
          <IconHeart :fill="liked"/>
        </button>
        <nuxt-link to="/auth/signIn" class="bg-white rounded-lg p-3 ">
          <img src="~/assets/svg/Profile.svg">
        </nuxt-link>
      </div>
    </div>
    <div class="px-80 py-4  border-b border-gray-200 flex items-center justify-between bg-white">
      <div class="flex items-center">
        <div class="w-44">
          <DropDown :source="items" :selected="selected"
                    :class-button="'rounded-lg border border-light-gray'"></DropDown>
        </div>
        <div class="flex items-center gap-10 text-sm text-tertiary ml-10">
          <nuxt-link :to="item.to" v-for="item in tabs">
            {{ item.name }}
          </nuxt-link>
        </div>
      </div>
      <div>
        <span class="text-sm">
          <span class="text-tertiary font-light mr-2">
            Contac:
          </span>
          (808) 555-0111
        </span>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  components: {
    IconHeart: () => import('~/components/icon/heart.vue'),
    DropDown: () => import('~/components/DropDown.vue'),

  },
  data() {
    return {
      search: null,
      buyCount: 2,
      liked: false,
      items: [
        'All Categories', 'item1', 'item2', 'item3', 'item4'
      ],
      selected: 'All Categories',
      tabs: [
        {
          name: 'Home',
          to: '/'
        },
        {
          name: 'Shop',
          to: '/shop'
        },
        {
          name: 'Product',
          to: '/product'
        },
        {
          name: 'Pages',
          to: '/pages'
        },
        {
          name: 'About',
          to: '/about'
        }
      ]
    }
  }
}
</script>
<style>
input:focus {
  outline: none;
}

.router-link-exact-active {
  color: #007580 !important;
}
</style>
