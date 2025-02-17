<script setup>
import { ref,onMounted, watch } from 'vue';
import RecipeList from './components/RecipeList.vue';
import RecipeForm from './components/RecipeForm.vue';
import RecipeDetails from './components/RecipeDetails.vue';

const recipes = ref([]);
const selectedRecipe = ref(null);

onMounted(() => {
  const savedRecipes = localStorage.getItem('recipes');
  if (savedRecipes) {
    recipes.value = JSON.parse(savedRecipes);
  }
});

watch(recipes, (newRecipes) => {
  localStorage.setItem('recipes', JSON.stringify(newRecipes));
}, { deep: true });

const addRecipe = (recipe) => {
  recipes.value.push(recipe);
};

const selectRecipe = (recipe) => {
  selectedRecipe.value = recipe;
};
</script>

<template>
  <div>
    <h1>Recipe Tracker</h1>
    <RecipeList :recipes="recipes" @select-recipe="selectRecipe" :selectedRecipe="selectedRecipe" />
    <RecipeForm @add-recipe="addRecipe" />
    <RecipeDetails v-if="selectedRecipe" :recipe="selectedRecipe" />
  </div>
</template>