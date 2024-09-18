<template>
    <div class="category-filter">
      <select v-model="selectedCategory" @change="filterByCategory">
        <option value="">Todas as Categorias</option>
        <option v-for="category in categories" :key="category" :value="category">
          {{ category }}
        </option>
      </select>
    </div>
  </template>
  
  <script>
  export default {
    name: 'CategoryFilter',
    props: {
      categories: Array
    },
    data() {
      return {
        selectedCategory: ''
      }
    },
    methods: {
      filterByCategory() {
        this.$emit('category-selected', this.selectedCategory)
      }
    }
  }
  </script>
  
  <style scoped>
  .category-filter {
    margin: 20px 0;
  }
  select {
    width: 100%;
    padding: 10px;
    font-size: 16px;
    border: 1px solid #ddd;
    border-radius: 4px;
  }
  </style>