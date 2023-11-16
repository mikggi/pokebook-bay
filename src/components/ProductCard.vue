<script setup>

defineProps({
  book: {
    type: Object,
    required: true,
  }

  
})

</script>

<template>
  <RouterLink :to="{ name: 'book-details', params: { id: book.id } }">
    <div class="product-card">
      <img :src="book.image" alt="image" />
      <h2>{{ book.title }}</h2>
    </div>
  </RouterLink>
</template>

<style scoped>
a {
  text-decoration: none;
  color: Black;
  font-weight: bolder;
}
.product-card {

  text-decoration: none;
  width:200px; 
  max-height: 200px; 
  box-sizing: content-box; 
  cursor: pointer;
  border: 3px solid #39495c;
  background-color: whitesmoke;
  margin-top:  18px;
  margin-bottom: 18px;
  display: flex;
  flex-direction: column-reverse;
  align-items: center; 
  
}

.product-card:hover {
  transform: scale(1.1);
}
.product-card img {
  max-width: 100px; 
  max-height: 100px;
  margin-bottom: 20px; 
}
</style>