<template>
  <div>
    <div class="overflow-x-hidden" style="padding-top: 206px">
      <layout-header class="fixed w-full top-0 z-50"/>
      <slot class="relative overflow-x-hidden w-full" />
      <layout-footer class=""/>
    </div>
  </div>
</template>
<script setup>
import { ref } from 'vue'
const route = useRoute()
const layout = ref('default')
</script>

