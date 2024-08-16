<script setup>
import SingleCard from './SingleCard.vue'

defineProps({
  items: Array
})

const onClickFavorite = (singleItem, items) => {
  items.forEach((item) => {
    if (item.id === singleItem.id) {
      item.isFavorite = !item.isFavorite
    }
  })
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
      :onClickFavorite="() => onClickFavorite(item, items)"
      :imageUrl="item.imageUrl"
      :title="item.title"
      :price="item.price"
      :isAdded="item.isAdded"
      :onClickAdd
    />
  </div>
</template>
