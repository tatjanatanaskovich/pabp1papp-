<template>
  <div class="container">
    <Header />
    <CategoryTable />
    <ProductTable />
    
  </div>
  <Footer />
</template>

<script>
  import Header from './components/Header.vue'
  import ProductTable from './components/ProductTable.vue'
  import CategoryTable from './components/CategoryTable.vue'
  import Footer from './components/Footer.vue'

  export default {
    name: 'App',
    components: {
      Header,
      CategoryTable,
      ProductTable,
      Footer
    }
  }
</script>

<style>
  #app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    /* text-align: center; */
    /* color: #2c3e50;
    margin-top: 60px;
    padding-left: 50px; */
  }
  .container {
    background-color:beige;
    color: #2c3e50;
    margin-top: 60px;
    padding-left: 50px;
  }
</style>
