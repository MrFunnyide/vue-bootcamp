<script setup>
import { ref } from 'vue';
import ItemsCard from './card/ItemsCard.vue';

const newItem = ref([
   { id: 1, title: 'Mobile UI Kit', text: 'Mobile UI Kit', image: 'items-1.jpg' },
   { id: 2, title: 'Online Doctor Consultation', text: 'Website UI Kit', image: 'items-2.jpg' },
   { id: 3, title: 'Banking Crypto', text: 'Mobile UI Kit', image: 'items-3.jpg' }

])
</script>
<template>
   <div class="container px-4 mx-auto my-16 md:px-12">
      <h2 class="mb-4 text-xl font-medium md:mb-0 md:text-lg">New Items</h2>
      <div class="flex flex-wrap -mx-1 lg:-mx-4">
         <ItemsCard v-for="data in newItem" :key="data.id" :title="data.title" :text="data.text" :image="data.image" />
      </div>
   </div>
</template>