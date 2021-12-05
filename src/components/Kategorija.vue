<template>
  <div id="mydiv">
    <h2>Izaberi kategoriju</h2>
    <label>Izaberi jednu od kategorija</label>
    <select v-model="kategorija.categoryName" @click="GetCategories()">
      <option v-for="kategorija in kategorije" :key="kategorija.categoryId">{{kategorija.categoryName}}</option>
    </select>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  name: 'Kategorija',
    data () {
      return {
        kategorija: {
          categoryId: 0,
          categoryName: String,
          description: String,
          products: []
        },
        kategorije: [],
      }
    },
 
    methods: {
      GetCategories(){
        axios.get('http://94.156.189.137:8000/api/Categories')
        .then((response)=> {
          this.kategorije = response.data;
          console.log('kategorije: ' + JSON.stringify(this.kategorije));
        })
        .catch(function (error){
          console.log(error);
        })
      },
      
    },
}
</script>

<style>
#mydiv {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #000;
  margin-top: 60px;
}
</style>