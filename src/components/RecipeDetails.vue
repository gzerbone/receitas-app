<template>
  <div v-if="recipe" class="recipe-details">
    <h2>{{ recipe.name }}</h2>
    <h3>Ingredientes:</h3>
    <ul>
      <li v-for="(ingredient, index) in recipe.ingredients" :key="index">
        {{ ingredient }}
      </li>
    </ul>
    <h3>Instruções:</h3>
    <p>{{ recipe.instructions }}</p>
  </div>
</template>

<script>
export default {
  name: 'RecipeDetails',
  props: {
    recipe: Object
  }
}
</script>

<style scoped>
.recipe-details {
  margin: 20px;
  padding: 20px;
  border: 1px solid #ddd;
}
</style>