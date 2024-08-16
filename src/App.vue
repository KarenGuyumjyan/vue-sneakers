``<script setup>
import { ref, onMounted, watch } from 'vue'

import Header from './components/Header.vue'
import CardList from './components/CardList.vue'
import DrawerCart from './components/DrawerCart.vue'
import axios from 'axios'

const openDrawer = ref(false)
const items = ref([])
const sortBy = ref('')
const searchQuery = ref('')

const handleOpenDrawer = () => {
  openDrawer.value = !openDrawer.value
}

const onChangeSelect = (event) => {
  sortBy.value = event.target.value
}

const onSearch = (event) => {
  searchQuery.value = event.target.value
}

onMounted(async () => {
  const { data } = await axios.get('https://49fccd1bc666e8dd.mokky.dev/items')
  items.value = data
})

watch(sortBy, async () => {
  const { data } = await axios.get(
    'https://49fccd1bc666e8dd.mokky.dev/items?sortBy=' + sortBy.value
  )
  items.value = data
})

watch(searchQuery, async () => {
  const { data } = await axios.get(
    'https://49fccd1bc666e8dd.mokky.dev/items?title=*' + searchQuery.value + '*'
  )
  items.value = data
})
</script>

<template>
  <div class="bg-zinc-50 2xs:w-5/6 xs:w-full rounded-xl shadow-xl m-auto 2xs:my-16 xs:my-0">
    <div v-if="openDrawer">
      <DrawerCart :handleOpenDrawer />
    </div>
    <Header :handleOpenDrawer />
    <div
      class="lg:p-10 md:p-8 p-6 flex flex-col-reverse sm:flex-row gap-5 justify-between items-center"
    >
      <h2 class="text-2xl font-bold">All Sneakers</h2>
      <div class="w-full sm:w-fit flex flex-col md:flex-row gap-4 md:gap-10">
        <select
          class="text-gray-500 bg-transparent border border-slate-200 rounded-[10px] px-3 py-2 outline-none focus:border-gray-400"
          @change="onChangeSelect"
        >
          <option value="id">Popular</option>
          <option value="title">Name</option>
          <option value="price">Price Low -> High</option>
          <option value="-price">Price High -> Low</option>
        </select>
        <div class="relative">
          <img src="/public/search.svg" alt="Search" class="absolute top-2.5 left-3" />
          <input
            class="text-gray-500 w-full bg-transparent border border-slate-200 rounded-[10px] py-1.5 pl-9 pr-4 outline-none focus:border-gray-400"
            placeholder="Search..."
            @change="onSearch"
          />
        </div>
      </div>
    </div>
    <CardList :items="items" />
  </div>
</template>
