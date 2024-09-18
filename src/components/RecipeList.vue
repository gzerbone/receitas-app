<template>
    <div class="recipe-list">
      <h2>Lista de Receitas</h2>
      <SearchBar @search="filterRecipes" />
      <CategoryFilter :categories="uniqueCategories" @category-selected="filterByCategory" />
      <ul>
        <li v-for="recipe in filteredRecipes" :key="recipe.id" @click="selectRecipe(recipe)">
          {{ recipe.name }} ({{ recipe.category }})
        </li>
      </ul>
    </div>
</template>

  <script>
    import SearchBar from './SearchBar.vue'
    import CategoryFilter from './CategoryFilter.vue'

    export default {
    name: 'RecipeList',
    components: {
        SearchBar,
        CategoryFilter
    },
    data() {
      return {
        recipes: [
        { id: 1, name: 'Bolo de Chocolate', category: 'Sobremesa', ingredients: ['Farinha', 'Chocolate', 'Ovos', 'Açúcar'], instructions: 'Misture tudo e asse por 30 minutos.' },
        { id: 2, name: 'Salada Caesar', category: 'Salada', ingredients: ['Alface', 'Croutons', 'Frango', 'Molho Caesar'], instructions: 'Misture os ingredientes e sirva.' },
        { id: 3, name: 'Lasanha', category: 'Prato Principal', ingredients: ['Massa de lasanha', 'Carne moída', 'Molho de tomate', 'Queijo'], instructions: 'Monte as camadas e asse por 45 minutos.' },
        ],
        searchTerm: '',
        selectedCategory: '',
      }
    },
    computed: {
    uniqueCategories() {
      return [...new Set(this.recipes.map(recipe => recipe.category))]
    },
    filteredRecipes() {
      return this.recipes.filter(recipe => 
        recipe.name.toLowerCase().includes(this.searchTerm.toLowerCase()) &&
        (this.selectedCategory === '' || recipe.category === this.selectedCategory)
      )
    }
  },
  methods: {
    selectRecipe(recipe) {
      this.$emit('recipe-selected', recipe)
    },
    filterRecipes(term) {
      this.searchTerm = term
    },
    filterByCategory(category) {
      this.selectedCategory = category
    }
  }
}
</script>
  
<style scoped>
.recipe-list {
  max-width: 800px;
  margin: 20px auto;
  padding: 20px;
  background-color: #f9f9f9;
  border-radius: 8px;
  box-shadow: 0 2px 4px rgba(0,0,0,0.1);
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  cursor: pointer;
  padding: 15px;
  border: 1px solid #ddd;
  margin-bottom: 10px;
  border-radius: 4px;
  transition: background-color 0.3s ease;
}
li:hover {
  background-color: #e9e9e9;
}
button {
  background-color: #4CAF50;
  color: white;
  padding: 10px 15px;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  transition: background-color 0.3s ease;
}
button:hover {
  background-color: #45a049;
}
.pagination {
  display: flex;
  justify-content: center;
  align-items: center;
  margin-top: 20px;
}
.pagination button {
  margin: 0 10px;
}
</style>