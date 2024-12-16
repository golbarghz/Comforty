<template>
  <div class="px-28">
    <div class="underlayer bg-light-gray py-10 px-20">
      <UBreadcrumb :links="links" :ui="{ li:'text-sm text-tertiary font-normal',  active: 'text-dark-blue font-medium', base:'font-normal'
}"/>
      <p class="text-2xl text-dark-blue mt-6 font-semibold">Sign In</p>
    </div>
    <div class="flex items-center justify-center my-24">
      <div class="rounded-xl p-8 flex flex-col" style="box-shadow: 0px 0px 30px 0px rgba(39, 35, 67, 0.12);">
        <p class="text-3xl text-dark-blue font-semibold text-center">Sign In</p>
        <input v-model="email"
               placeholder="Email"
               class="py-3 px-4 rounded-lg bg-light-gray mt-6" style="width: 584px"/>
        <div class="py-3 px-4 rounded-lg bg-light-gray mt-4 flex justify-between items-center" style="width: 584px">
          <input v-model="password" type="password"
                 placeholder="Password" class="bg-light-gray"
          />
          <img src="~/assets/svg/Eye.svg">
        </div>
        <div class="flex justify-between items-center mt-4">
          <UCheckbox label="Remember me" :ui="{ label:'text-sm text-tertiary font-normal',}"/>
          <button style="color: #007580" class="text-sm">Forget Password</button>
        </div>
        <button class="bg-secondary rounded-lg text-white flex gap-3 items-center justify-center p-3 mt-6"
                style="width: 584px">
          Sign In
          <img src="~/assets/svg/Right.svg">
        </button>
        <div class="flex items-center justify-center gap-1 text-sm text-dark-blue mt-6">
          Don’t have account?
          <button style="color: #007580" class="text-sm">Sign Up</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import {ref} from "vue";

useHead({
  title: "Sign In",
});
const links = [{
  label: 'Home',
  to: '/'
}, {
  label: 'Auth',
}, {
  label: 'Sign In',
  to: '/auth/signIn'
}]
const email = ref()
const password = ref()

</script>

<style scoped>
.underlayer {
  height: 156px;
  border-bottom-right-radius: 20px;
  border-bottom-left-radius: 20px;
}
</style>