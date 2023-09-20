<script>
import BookItem from './components/BookItem.vue';
import CartBooks from './components/CartBooks.vue';
import info from './components/data.json';
import { ref } from 'vue';
const cartItems = ref([]);

export default {
  data() {
    return {
      cartItems: [],
      info,
    };
  },
  components: {
    BookItem,
    CartBooks,
  },
};
</script>
<template>
  <div class="container mx-auto my-4">
    <div class="grid grid-cols-10">
      <div
        class="
          col-span-10
          sm:col-start-2 sm:col-span-8
          lg:col-start-3 lg:col-span-6
        "
      >
        <div class="sm:grid sm:grid-cols-2 gap-2">
          <div>
            <h4 class="font-bold text-3xl m-auto text-center">All Books</h4>
            <div v-for="(book, index) of info.books">
              <BookItem
                :book="book"
                :index="index"
                @addToCart="
                  (val) => {
                    cartItems[index] = val;
                  }
                "
              />
            </div>
          </div>
          <div>
            <h4 class="font-bold text-3xl m-auto text-center">Cart Items</h4>
            <CartBooks :cartItems="cartItems" />
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
