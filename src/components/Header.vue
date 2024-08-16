<script setup>
defineProps({
  handleOpenDrawer: Function
})
</script>

<template>
  <header
    class="xs:px-4 xs:py-6 2xs:p-10 border-b-2 flex gap-8 flex-col 2xs:flex-row justify-between items-center"
  >
    <div class="flex gap-4 cursor-pointer">
      <img src="/public/logo.png" alt="Logo" class="w-10, h-10" />
      <div>
        <p class="text-xl font-bold">Vue Sneakers</p>
        <p class="text-sm font-normal text-gray-400">The best sneakers store</p>
      </div>
    </div>
    <ul class="flex gap-8 xs:gap-4 flex-col sm:flex-row xs:flex-row 2xs:flex-col">
      <li class="flex gap-2 items-center cursor-pointer" @click="handleOpenDrawer">
        <img src="/public/cart.svg" alt="Price" class="w-4 h-4" />
        <b class="text-sm text-gray-500 hover:text-black">100$</b>
      </li>
      <li class="flex gap-2 items-center cursor-pointer">
        <img src="/public/heart.svg" alt="Favorite" class="w-4 h-4" />
        <b class="text-sm text-gray-400 hover:text-black">Favorite</b>
      </li>

      <li class="flex gap-2 items-center cursor-pointer">
        <img src="/public/profile.svg" alt="Profile" class="w-4 h-4" />
        <b class="text-sm text-gray-400 hover:text-black">Profile</b>
      </li>
    </ul>
  </header>
</template>
