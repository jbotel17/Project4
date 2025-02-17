<script setup>
import { ref, defineEmits } from 'vue';

const emit = defineEmits(['add-recipe']);

const name = ref('');
const ingredients = ref([]);
const ingredientName = ref('');
const ingredientCost = ref(0);
const ingredientCalories = ref(0);

const addIngredient = () => {
  if (ingredientName.value) {
    ingredients.value.push({
      name: ingredientName.value,
      cost: Number(ingredientCost.value),
      calories: Number(ingredientCalories.value)
    });
    ingredientName.value = '';
    ingredientCost.value = 0;
    ingredientCalories.value = 0;
  }
};

const addRecipe = () => {
  if (name.value && ingredients.value.length > 0) {
    emit('add-recipe', { name: name.value, ingredients: ingredients.value });
    name.value = '';
    ingredients.value = [];
  }
};
</script>

<template>
    <div>
        <h3>Add New Recipe</h3>
        <input v-model="name" placeholder="Recipe Name" />
    
        <h4>Ingredients</h4>
        <input v-model="ingredientName" placeholder="Ingredient Name" />
        <input v-model.number="ingredientCost" type="number" placeholder="Cost ($)" />
        <input v-model.number="ingredientCalories" type="number" placeholder="Calories" />
        <button @click="addIngredient">Add Ingredient</button>

        <ul>
            <li v-for="item in ingredients" :key="item.name">
              {{ item.name }} - ${{ item.cost }} - {{ item.calories }} cal
            </li>
        </ul>

        <button @click="addRecipe">Add Recipe</button>
    </div>
</template>