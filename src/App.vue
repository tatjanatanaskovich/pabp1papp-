<template>
  <div class="container">
    <CategoryTable />
    <ProductTable />
  </div>
</template>

<script>
  import ProductTable from './components/ProductTable.vue'
  import CategoryTable from './components/CategoryTable.vue'

  export default {
    name: 'App',
    components: {
      ProductTable,
      CategoryTable
    }
  }
</script>

<style>
  #app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
  }
  .container {
    background-color:beige;
  }
</style>
