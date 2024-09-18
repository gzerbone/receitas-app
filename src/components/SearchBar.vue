<template>
    <div class="search-bar">
      <input 
        v-model="searchTerm" 
        @input="search"
        type="text" 
        placeholder="Pesquisar receitas..."
      >
    </div>
  </template>
  
  <script>
  export default {
    name: 'SearchBar',
    data() {
      return {
        searchTerm: ''
      }
    },
    methods: {
      search() {
        this.$emit('search', this.searchTerm)
      }
    }
  }
  </script>
  
  <style scoped>
  .search-bar {
    margin: 20px 0;
  }
  input {
    width: 100%;
    padding: 10px;
    font-size: 16px;
    border: 1px solid #ddd;
    border-radius: 4px;
  }
  </style>