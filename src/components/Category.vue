<template class="category">
  <p><b>Ovo je komonenta Category</b></p>
  <p>Dobijanje metodom GET liste sa svim kategorijama. 
    Klikom na dugme prikazuju se sve kategorije.</p>
  <button @click="GetCategories()">Prikazi sve kategorije</button>
  <table>
    <th>
      <tr>
        <td>|</td>
        <td>Naziv Kategorije</td>
        <td>|</td>
        <td>ID Kategorije</td>
        <td>|</td>
        <td>Opis Kategorije</td>
        <td>|</td>
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
      <!-- <td>
        <ul>
          <li v-for="category in categories" :key="category.products">{{category.products}}</li>
        </ul>
      </td>-->
      <td> 
        <ul>
          <li v-for="category in categories" :key="category.categoryId">{{category.description}}</li>
        </ul>
      </td>
      <td>
        <ul>
          <li>
            <button @click="GetProductsInCategory()">Prikazi sve proizvode iz odabrane kategorije</button>
          </li>
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
        products: [],
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
        },
        
        GetProductsInCategory(categoryId){
        axios.get(`http://94.156.189.137:8000/api/Categories/products/${categoryId}`)
          .then((response)=> {
            this.products = response.data;
          console.log('products: ' + JSON.stringify(this.products.categoryId));
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
  list-style-type:none;
}
</style>