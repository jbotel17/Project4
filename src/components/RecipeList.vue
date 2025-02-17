<script setup>
import { defineProps, defineEmits } from 'vue';

const props = defineProps({
    recipes: Array,
    selectedRecipe: Object,
})

const emit = defineEmits(['select-recipe']);

const selectRecipe = (recipe) => {
  emit('select-recipe',recipe);
};
</script>

<template>
 <div>
    <h2>Recipe List</h2>
    <ul>
      <li 
      v-for="recipe in recipes" 
      :key="recipe.name" 
      @click="selectRecipe(recipe)">
        {{ recipe.name }}
      </li>
    </ul>
    <RecipeDetails v-if="props.selectedRecipe" :recipe="props.selectedRecipe" />
 </div>
</template>