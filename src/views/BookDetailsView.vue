<script setup>
import { ref, onMounted } from 'vue'
import BookService from '@/services/BookService.js'

const theBook = ref(null)

const props = defineProps({
    id: { required: true }
})

onMounted(() => {
    BookService.getBook(props.id)
    .then((response)=>{
        theBook.value = response.data
    })
    .catch((error)=>{
        console.log(error)
    })
})
</script>

<template>
    <div v-if="theBook">
        <h1>{{  theBook.title }}</h1>
        <p>{{ theBook.type1 }} / {{ theBook.type2 }} Type </p>
        <p2>Japanese Name: {{ theBook.jpname }}<br></p2>
        <p2>Region: {{ theBook.region }} <br></p2>
        <p2>Evolution: {{ theBook.Evolution }} <br></p2>
        <p2>Fun Fact: {{ theBook.funfact }} </p2>
    </div>
</template>

<style scoped>
div {
  box-sizing: content-box;
  margin: 10% auto;
  padding: 20px;
  max-width: 600px;
  border: 2px double black;
  border-radius: 8px;
  background-color: #f9f9f9;
}

/* Headings */
h1 {
  font-size: 2em;
  color: #333;
  text-align: center;
  font-weight: bolder;
}

/* Paragraphs */
p {
  font-size: 1.7em;
  line-height: 1.6;
  color: grey;
  text-align: center;
  
}

p2{
  font-size: 1em;
  line-height: 1.6;
  color: darkslategrey;
  text-align: center;
  font-weight: bold;
  
}
</style>