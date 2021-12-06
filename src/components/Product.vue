<template class="product">
  <p><b>Ovo je komonenta Product</b></p>
  <p>Dobijanje metodom GET liste sa svim proizvodima</p>
  <button @click="GetProducts()">Prikazi sve proizvode</button>
  <table>
    <th>
      <tr>
        <td>Naziv Proizvoda</td>
        <td>ID Proizvoda</td>
        <td>Opis Proizvoda</td>
      </tr>
    </th>
    <tr>
      <td>
        <ol>
          <li v-for="product in products" :key="product.productId">{{product.productName}}</li>
        </ol>
      </td>
      <td>
        <ul>
          <li v-for="product in products" :key="product.productId">{{product.productId}}</li>
        </ul>
      </td>
      <td>
        <ul>
          <li v-for="product in products" :key="product.productId">{{product.description}}</li>
        </ul>
      </td>
    </tr>
  </table>
</template>

<script>
  import axios from 'axios'
  export default {
    name: 'Product',

    data () {
      return {
        products: [],
      }
    },

    methods: {
      GetProducts(){
        axios.get(`http://94.156.189.137:8000/api/Products`)
          .then((response)=> {
            this.products = response.data;
          console.log('products: ' + JSON.stringify(this.products));
          })
          .catch(function (error){
            console.log(error);
          })
      }
    },

  }
</script>

<style>
.product {
  color: greenyellow;
  font-style: oblique;
  background-color: black;
  text-align: left;
}
</style>