<script>
export default {
  data() {
    return {
      items: [],
    };
  },
  props: ['cartItems'],
  watch: {
    cartItems: {
      handler: function () {
        this.items = this.cartItems.filter((item) => item !== null);
      },
      deep: true,
    },
  },
};
</script>
<template>
  <div class="card p-6 border rounded-lg" v-if="cartItems.length > 0">
    <ul class="text-center p-4 text-lg">
      <li v-for="item of items">
        {{ item.title }} (Quantity: {{ item.stock }})
      </li>
    </ul>
  </div>
</template>
