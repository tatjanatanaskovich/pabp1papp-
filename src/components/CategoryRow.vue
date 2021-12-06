<template>
  <div id="mydiv">
    <label>Izaberi jednu od kategorija</label>
    <select v-model="category.categoryName" @click="GetCategories()">
      <option v-for="category in categories" :key="category.categoryId">{{category.categoryName}}</option>
    </select>
  </div>
</template>

<script>
  import axios from 'axios'
  export default {
    name: 'CategoryRow',
    
      data () {
        return {
          category: {
            categoryId: 0,
            categoryName: String,
            description: String
          },
          categories: [],
        }
      },
 
    methods: {

      GetCategories(){
        axios.get('http://94.156.189.137:8000/api/Categories')
        .then((response)=> {
          this.categories = response.data;
          console.log('categories: ' + JSON.stringify(this.categories));
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