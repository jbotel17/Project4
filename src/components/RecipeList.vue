<script setup>
import { ref } from 'vue';
import RecipeDetails from './RecipeDetails.vue';

const recipes = ref([
  { name: 'Pasta', ingredients: [{ name: 'Tomato Sauce', cost: 2, calories: 100 }, { name: 'Noodles', cost: 3, calories: 200 }] },
  { name: 'Salad', ingredients: [{ name: 'Lettuce', cost: 1, calories: 10 }, { name: 'Dressing', cost: 2, calories: 50 }] }
]);

const selectedRecipe = ref(null);

const selectRecipe = (recipe) => {
  selectedRecipe.value = recipe;
};
</script>

<template>
 <div>
    <h2>Recipe List</h2>
    <ul>
      <li v-for="recipe in recipes" :key="recipe.name" @click="selectRecipe(recipe)">
        {{ recipe.name }}
      </li>
    </ul>
    <RecipeDetails v-if="selectedRecipe" :recipe="selectedRecipe" />
 </div>
</template>