<template>
  <div id="app">
    <h1>Aplicativo de Receitas</h1>
    <div class="container">
      <RecipeList @recipe-selected="showRecipe" />
      <RecipeDetails :recipe="selectedRecipe" />
    </div>
  </div>
</template>

<script>
import RecipeList from './components/RecipeList.vue'
import RecipeDetails from './components/RecipeDetails.vue'

export default {
  name: 'App',
  components: {
    RecipeList,
    RecipeDetails
  },
  data() {
    return {
      selectedRecipe: null
    }
  },
  methods: {
    showRecipe(recipe) {
      this.selectedRecipe = recipe
    }
  }
}
</script>

<style>
#app {
  font-family: Arial, sans-serif;
  max-width: 800px;
  margin: 0 auto;
  padding: 20px;
}
.container {
  display: flex;
  justify-content: space-between;
}
h1, h2, h3 {
  color: #2c3e50;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  cursor: pointer;
  padding: 10px;
  border: 1px solid #ddd;
  margin-bottom: 5px;
  border-radius: 4px;
  transition: background-color 0.3s;
}
li:hover {
  background-color: #f0f0f0;
}
</style>