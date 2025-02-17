<script setup>
import { defineProps, computed } from 'vue';

const props = defineProps({
  recipe: Object,
});

const totalCost = computed(() => {
  return props.recipe.ingredients.reduce((sum, item) => sum + item.cost, 0);
});

const totalCalories = computed(() => {
  return props.recipe.ingredients.reduce((sum, item) => sum + item.calories, 0);
});
</script>

<template>
  <div v-if="props.recipe">
    <h3>{{ props.recipe.name }} - RecipeDetails</h3>
    <ul>
      <li v-for="item in props.recipe.ingredients" :key="item.name">
        {{ item.name }} - ${{ item.cost }} - {{ item.calories }} cal
      </li>
    </ul>
    <p><strong>Total Cost:</strong> ${{ totalCost }}</p>
    <p><strong>Total Calories:</strong> {{ totalCalories }} cal</p>
  </div>
</template>