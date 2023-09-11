<script setup>
import { ref, onMounted } from 'vue';
import { useRoute } from 'vue-router';
import ItemsCard from '../homepage/card/ItemsCard.vue';
import axios from 'axios';

const newItem = ref([]);
const route = useRoute();
const category = ref({});

//get data
async function getNewItems() {
   try {
      const response = await axios.get('https://zullkit-backend.demo.belajarkoding.com/api/categories?id=' + route.params.id + '&show_product=1');
      newItem.value = response.data.data.products;
      category.value = response.data.data;
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
      <h2 class="mb-4 text-xl font-medium md:mb-0 md:text-lg">{{ category.name }}</h2>
      <div class="flex flex-wrap -mx-1 lg:-mx-4">
         <ItemsCard v-for="data in newItem" :key="data.id" :id="data.id" :title="data.name" :description="data.subtitle"
            :image="data.thumbnails" />
      </div>
   </div>
</template>