<script setup>
import { ref, onMounted } from 'vue';
import axios from 'axios';
import CategoriesCard from '../homepage/card/CategoriesCard.vue';

const categories = ref([]);

// get data
async function getDataCategories() {
   try {
      const response = await axios.get('https://zullkit-backend.demo.belajarkoding.com/api/categories?limit=1000');
      categories.value = response.data.data.data;
   } catch (error) {
      console.log(error);
   }
}

// onMounted data categori
onMounted(() => {
   getDataCategories();
})


</script>
<template>
   <div class="container px-4 mx-auto my-16 md:px-12" id="categories">
      <h2 class="mb-4 text-xl font-medium md:mb-0 md:text-lg">All Categories</h2>
      <div class="flex flex-wrap -mx-1 lg:-mx-4">
         <CategoriesCard v-for="data in categories" :id="data.id" :key="data.id" :title="data.name"
            :count="data.products_count" :image="data.thumbnails" />
      </div>
   </div>
</template>