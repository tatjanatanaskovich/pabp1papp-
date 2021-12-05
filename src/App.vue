<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <Proizvod />
</template>

<script>
import Proizvod from './components/Proizvod.vue'

export default {
  name: 'App',
  components: {
    Proizvod
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
