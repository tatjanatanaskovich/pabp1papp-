<template>
  <Kategorija />
  <ProductTable />

</template>

<script>
import ProductTable from './components/ProductTable.vue'
import Kategorija from './components/Kategorija.vue'


export default {
  name: 'App',
  components: {
    ProductTable,
    Kategorija
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
</style>
