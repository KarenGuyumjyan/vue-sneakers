<script setup>
defineProps({
  isFavorite: Boolean,
  onClickFavorite: Function,
  imageUrl: String,
  title: String,
  price: Number,
  isAdded: Boolean,
  onClickAdd: Function
})
</script>

<template>
  <div class="flex justify-center">
    <div
      class="bg-white w-screen md:max-w-[220px] max-w-fit h-full md:max-h-[260px] max-h-fot md:border md:rounded-[40px] relative flex flex-col items-center gap-3.5 hover:-translate-y-2 hover:shadow-lg transition"
    >
      <img
        :src="isFavorite ? '/public/like-2.svg' : '/public/like-1.svg'"
        alt="Favorite"
        class="absolute md:left-7 md:top-7 left-5 top-5 cursor-pointer"
        @click="onClickFavorite"
      />
      <img :src="imageUrl" alt="Sneakers" class="w-4/6 pt-3 md:max-h-[140px]" />
      <p class="text-sm w-fit max-w-[150px] text-center">{{ title }}</p>
      <div class="w-full md:px-8 px-4 flex justify-between pb-6">
        <div class="max-h-8 flex flex-col justify-center">
          <spans class="text-xs text-gray-300">PRICE: </spans>
          <span class="font-bold text-sm">{{ price }}$</span>
        </div>
        <img
          :src="isAdded ? '/public/checked.svg' : '/public/plus.svg'"
          alt="Add"
          class="cursor-pointer"
          @click="onClickAdd"
        />
      </div>
    </div>
  </div>
</template>
