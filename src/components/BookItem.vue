<script setup>
import { ref } from 'vue';
const props = defineProps(['book'])
const emit = defineEmits(['addToCart'])
const cartAddedBookes = ref([])
let count = ref(0)
function handleClick(title, stock) {
  if (count.value < stock) {
    count.value++;
    cartAddedBookes.value = { title: title, stock: count.value }
    emit('addToCart', cartAddedBookes.value)
    console.log(cartAddedBookes.value);
  }
}
</script>
<template>
  <div class="block rounded-lg p-6 border mb-2">
    <img class="m-auto h-[350px]" width="300" :src="book.image" alt="bookImg">
    <div class="my-2 text-center">
      <h5 class="mb-2 text-xl font-medium leading-tight text-neutral-800 dark:text-neutral-50">
        {{ book.title }}
      </h5>
      <p class="text-base text-neutral-600 dark:text-neutral-200">
        <strong>Author : </strong><span>{{ book.author }}</span>
      </p>
      <p class="text-base text-neutral-600 dark:text-neutral-200">
        <strong>Price : </strong><span>{{ book.price }}</span>
      </p>
      <p class="text-base text-neutral-600 dark:text-neutral-200">
        <strong>Stock : </strong><span>{{ book.stock }}</span>
      </p>
      <button type="button" :class="count == book.stock ? 'cursor-not-allowed' : 'bg-green-600'"
        :disabled="count == book.status ? true : false" class="inline-block rounded text-white bg-green-600 p-2 mt-2"
        @click="handleClick(book.title, book.stock)">
        Add To Cart
      </button>
    </div>
  </div>
</template>
