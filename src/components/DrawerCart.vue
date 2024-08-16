<script setup>
import DrawerHeader from './DrawerHeader.vue'
import DrawerCartList from './DrawerCartList.vue'

defineProps({
  handleOpenDrawer: Function
})
</script>

<template>
  <div class="fixed top-0 left-0 w-screen h-full bg-black z-10 opacity-70"></div>
  <div class="fixed top-0 right-0 2xs:w-96 w-full h-full bg-white z-20 px-8 overflow-scroll">
    <DrawerHeader :handleOpenDrawer />
    <DrawerCartList />

    <div class="flex flex-col gap-3 pb-8 pt-4 bg-white sticky bottom-0">
      <div class="flex gap-2">
        <span>Total Price: </span>
        <div class="flex-1 border-b border-dashed"></div>
        <b>120 $</b>
      </div>
      <div class="flex gap-2">
        <span>Fees 5%: </span>
        <div class="flex-1 border-b border-dashed"></div>
        <b>6$</b>
      </div>
      <button
        :disabled="false"
        class="w-full py-4 rounded-2xl mt-3 transition text-white bg-lime-500 hover:bg-lime-600 active:bg-lime-700 disabled:bg-slate-300 cursor-pointer"
      >
        Confirm purchase
      </button>
    </div>
  </div>
</template>
