<template>
  <div class="product-container">
    <ProductCard
      v-for="book in books"
      :key="book.id"
      :book="book"
    />
  </div>
</template>

<script>
import ProductCard from '@/components/ProductCard.vue'; // adjust path as needed
import BookService from '@/services/BookService.js'; // adjust path as needed

export default {
  components: {
    ProductCard
  },
  data() {
    return {
      books: []
    };
  },
  async mounted() {
    try {
      const response = await BookService.getBooks();
      this.books = response.data;
    } catch (error) {
      console.error(error);
    }
  }
};
</script>
<style>
.product-container {
  display: flex;
  flex-wrap: wrap;
  width: 800px;
  margin: auto;
  justify-content: center;
  justify-content: space-around;
}
</style>