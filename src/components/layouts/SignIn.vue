<script setup>
import { RouterLink } from 'vue-router';
import SignUp from './SignUp.vue';

</script>
<template>
   <div class="md:order-2">
      <RouterLink to="/login"
         class="px-8 py-3 mt-2 mr-2 text-base font-medium text-black bg-gray-200 border border-transparent rounded-full hover:bg-gray-300 md:py-2 md:text-sm md:px-8 hover:shadow">
         Sign In
      </RouterLink>
      <SignUp />
   </div>
</template>