<script setup>
import { ref, onMounted } from 'vue';
import ItemsCard from './card/ItemsCard.vue';
import axios from 'axios';

const newItem = ref([])

//get data
async function getNewItems() {
   try {
      const response = await axios.get('https://zullkit-backend.demo.belajarkoding.com/api/products');
      newItem.value = response.data.data.data;
   } catch (error) {
      console.log(error);
   }
}

// mounted data products
onMounted(() => {
   getNewItems();
})


</script>
<template>
   <div class="container px-4 mx-auto my-16 md:px-12">
      <h2 class="mb-4 text-xl font-medium md:mb-0 md:text-lg">New Items</h2>
      <div class="flex flex-wrap -mx-1 lg:-mx-4">
         <ItemsCard v-for="data in newItem" :key="data.id" :id="data.id" :title="data.name" :description="data.subtitle"
            :image="data.thumbnails" />
      </div>
   </div>
</template>