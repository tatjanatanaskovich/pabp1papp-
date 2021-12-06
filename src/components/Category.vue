<template class="category">
  <p><b>Ovo je komonenta Category</b></p>
  <p>Dobijanje GET liste kategorija</p>
  <button @click="GetCategories()">Prikazi sve kategorije</button>
  <table>
    <th>
      <tr>
        <td>Naziv Kategorije</td>
        <td>ID Kategorije</td>
        <td>Opis Kategorije</td>
      </tr>
    </th>
    <tr>
      <td>
        <ol>
          <li v-for="category in categories" :key="category.categoryId">{{category.categoryName}}</li>
        </ol>
      </td>
      <td>
        <ul>
          <li v-for="category in categories" :key="category.categoryId">{{category.categoryId}}</li>
        </ul>
      </td>
      <td>
        <ul>
          <li v-for="category in categories" :key="category.categoryId">{{category.description}}</li>
        </ul>
      </td>
    </tr>
  </table>
</template>

<script>
  import axios from 'axios'
  export default {
    name: 'Category',

    data () {
        return {
          categories: [],
        }
      },

    methods: {
      GetCategories(){
        axios.get(`http://94.156.189.137:8000/api/Categories`)
          .then((response)=> {
            this.categories = response.data;
          console.log('categories: ' + JSON.stringify(this.categories));
          })
          .catch(function (error){
            console.log(error);
          })
        }
      }
  }
</script>

<style>
.category {
  color:rosybrown;
  font-style: oblique;
  background-color: black;
  text-align: left;
}
</style>