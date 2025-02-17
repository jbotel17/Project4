<script setup>
import { computed } from 'vue';

defineProps(['recipe']);

const totalCost = computed(() => {
  return props.recipe.ingredients.reduce((sum, item) => sum + item.cost, 0);
});

const totalCalories = computed(() => {
  return props.recipe.ingredients.reduce((sum, item) => sum + item.calories, 0);
});
</script>

<template>
  <div>
    <h3>RecipeDetails</h3>
    <ul>
      <li v-for="item in recipe.ingredients" :key="item.name">
        {{ item.name }} - ${{ item.cost }} - {{ item.calories }} cal
      </li>
    </ul>
    <p><strong>Total Cost:</strong> ${{ totalCost }}</p>
    <p><strong>Total Calories:</strong> {{ totalCalories }} cal</p>
  </div>
</template>