<script setup>
import { ref } from 'vue';
import RecipeList from './components/RecipeList.vue';
import RecipeForm from './components/RecipeForm.vue';

const recipes = ref([]);

const addRecipe = (recipe) => {
  recipes.value.push(recipe);
};
</script>

<template>
  <div>
    <h1>Recipe Tracker</h1>
    <RecipeList :recipes="recipes" />
    <RecipeForm @add-recipe="addRecipe" />
  </div>
</template>