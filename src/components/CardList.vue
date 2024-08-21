<script setup>
import SingleCard from './SingleCard.vue'

defineProps({
  items: Array
})

const handleFavoriteItem = (item) => {
  if (localStorage.favorites.includes(String(item.id))) {
    const favorites = localStorage.favorites.split(',')
    localStorage.favorites = favorites.filter((id) => id !== String(item.id))
    item.isFavorite = false
  } else {
    if (localStorage.favorites) {
      localStorage.favorites = localStorage.favorites + ',' + item.id
    } else {
      localStorage.favorites = item.id
    }
    item.isFavorite = true
  }
}

const onClickAdd = () => {
  alert(111)
}
</script>

<template>
  <div
    class="xl:p-16 xl:pt-0 lg:p-10 lg:pt-0 md:p-4 md:pt-0 g:p-10 grid lg:gap-7 gap-5 lg:grid-cols-4 sm:grid-cols-3 grid-cols-2"
  >
    <SingleCard
      v-for="item in items"
      :key="item.id"
      :isFavorite="item.isFavorite"
      :onClickFavorite="() => handleFavoriteItem(item)"
      :imageUrl="item.imageUrl"
      :title="item.title"
      :price="item.price"
      :isAdded="item.isAdded"
      :onClickAdd="onClickAdd"
    />
  </div>
</template>
