<script setup>
import { ref } from 'vue';
import RecipeList from './components/RecipeList.vue';
import RecipeForm from './components/RecipeForm.vue';

const recipes = ref([]);


</script>

<template>
  <div>
    <h1>Recipe Tracker</h1>
    <RecipeList :recipes="recipes" />
  
  </div>



</template>