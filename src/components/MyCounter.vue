<!-- <script>
export default {
  data() {
    return {
      count: 0
    }
  },

  methods: {
    increment() {
      this.count++
    },
    decrement() {
      this.count--
    }
  }
}
</script> -->

<script setup>
import { ref } from 'vue'

// let count = 0
const count = ref(0)

function increment() {
  count.value++
}

const decrement = () => {
  count.value--
}

const updateCount = (e) => {
  if (e.target.value) {
    count.value = e.target.value
  } else {
    count.value = 0
  }
}
</script>

<template>
  <h1 v-if="count > 0" class="counter-plus">{{ count }}</h1>
  <h1 v-else-if="count < 0" class="counter-minus">{{ count }}</h1>
  <h1 v-else>{{ count }}</h1>
  <button @click="decrement">-</button>
  <button @click="increment">+</button>
  <input @input="updateCount" type="number" :value="count" />
  <input v-model="count" />
</template>

<style scoped>
.counter-plus {
  color: green;
}
.counter-minus {
  color: red;
}
</style>
