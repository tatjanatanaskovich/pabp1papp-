<template class="product">
  <p><b>Ovo je komonenta Product</b></p>
  <p>Dobijanje metodom GET liste sa svim proizvodima. 
    Klikom na dugme prikazuju se svi proizvodi.</p>
  <button @click="GetProducts()">Prikazi sve proizvode</button>
  <table>
    <th>
      <tr>
        <td><ul><li style="list-style-type: none;">Naziv Proizvoda</li></ul></td>
        <td><ul><li style="list-style-type: none;">ID Proizvoda</li></ul></td>
        <td><ul><li style="list-style-type: none;">Cena Proizvoda u dinarima - RSD</li></ul></td>
        <td><ul><li style="list-style-type: none;">Kontrole</li></ul></td>
      </tr>
    </th>

    <div>
      <input type="text" v-model="newProduct.productName">
      <button @click="AddNewProduct()">Dodaj proizvod</button>
      <p>Prikaz testiranja radi: Proizvod {{newProduct.productName}} je dodat!</p>
    </div>
    

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
          <li v-for="product in products" :key="product.productId" style="list-style-type: none;">{{product.unitPrice}} RSD</li>
        </ul>
      </td>
      <td>
        <ul>
          <li v-for="product in products" :key="product.productId" style="list-style-type: none;">
          </li>
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
        newProduct:{}
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
      },
      AddNewProduct(){
        this.product.id = undefined;
        axios.post(`http://94.156.189.137:8000/api/Products`,this.newProduct)
        .then((response)=> {
          console.log(response)
          this.newProduct.productId=response.data.productId
          this.products.push(this.newProduct)
          this.newProduct={}
        
          })
          .catch(function (error){
            console.log(error);
          })
      }
    },
    // ako hocemo da se pri mauntovanju odmah prikazuju svi proizvodi
    // mounted(){
    //     this.GetProducts()
    // }

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