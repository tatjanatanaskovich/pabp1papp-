<template>
  <div class="container">
    <Header />
    <Category />
    <Product />
  </div>
  <Footer />
</template>

<script>
  import Header from './components/Header.vue'
  import Product from './components/Product.vue'
  import Category from './components/Category.vue'
  import Footer from './components/Footer.vue'

  export default {
    name: 'App',
    components: {
      Header,
      Category,
      Product,
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
