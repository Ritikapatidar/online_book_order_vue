<script setup>
import { watchEffect, ref } from 'vue';
const props = defineProps(['cartItems'])
let items = ref([])
watchEffect(() => {
    items.value = props.cartItems.filter((item) => item !== null)
})
</script>
<template>
    <div class="card p-6 border rounded-lg" v-if="cartItems.length > 0">
        <ul class="text-center p-4 text-lg">
            <li v-for="item of items">{{ item.title }} (Quantity: {{ item.stock }})</li>
        </ul>
    </div>
</template>