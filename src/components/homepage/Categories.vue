<script setup>
import { ref, onMounted } from 'vue';
import axios from 'axios';
import CategoriesCard from './card/CategoriesCard.vue';

// get data
function getDataCategories() {
   const dataCategories = axios.get('https://zullkit-backend.demo.belajarkoding.com/api/categories');
   console.log(dataCategories);
}

// onMounted data categori
onMounted(() => {
   getDataCategories();
})

const categories = ref([
   { id: 1, title: 'Mobile UI Kit', count: 731, image: 'categories-1.jpg' },
   { id: 2, title: 'Fonts', count: 657, image: 'categories-2.jpg' },
   { id: 3, title: 'Icon Set', count: 83.559, image: 'categories-3.jpg' },
   { id: 4, title: 'Website UI Kit', count: 4.500, image: 'categories-4.jpg' }
])

</script>
<template>
   <div class="container px-4 mx-auto my-16 md:px-12" id="categories">
      <h2 class="mb-4 text-xl font-medium md:mb-0 md:text-lg">Top Categories</h2>
      <div class="flex flex-wrap -mx-1 lg:-mx-4">
         <CategoriesCard v-for="data in categories" :key="data.id" :title="data.title" :count="data.count"
            :image="data.image" />
      </div>
   </div>
</template>