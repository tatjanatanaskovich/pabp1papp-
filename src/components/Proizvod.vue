<template>
  <div>
    <h2>Prikaži proizvod</h2>
    <button @click="GetProducts()" v-for="proizvod in proizvodi" :key="proizvod.productId">
      Prikazi proizvod
    </button>
    <h2>Unos proizvoda</h2>
    <div id="unos_proizvoda">
      <div>
        <label for="">Naziv proizvoda </label>
        <input type="text" v-model="proizvod.productName">
      </div>
      <div>
        <label for="">Cena proizvoda </label>
        <input type="number" v-model="proizvod.unitPrice">
      </div>
      <div>
        <label for="">Količina proizvoda </label>
        <input type="number" v-model="proizvod.unitsInStock">
      </div>
      <div>
        <button @click="UnesiProizvod()" :disabled="ProveriUnos">Unesi proizvod</button>
      </div>
    </div>
    <h2>Prikaz proizvoda</h2>
    <div>
      <table>
        <th>
          <td>Naziv proizvoda</td>
          <td>Raspoloživa količina proizvoda</td>
          <td>Cena proizvoda</td>
          <td>Ukupna vrednost proizvoda</td>
        </th>
        <tbody>
          <tr  v-for="(p,index) in proizvodi" :key="p">
            <td>{{ p.productName }}</td>
            <td>{{ p.unitsInStock }}</td>
            <td>{{ p.unitPrice }}</td>
            <td>{{ p.ukupnavrednost }}</td>
            <td><button @click="IzmeniProizvod(index)">Izmeni proizvod</button></td>
            <td><button @click="ObrisiProizvod(index)">Obriši proizvod</button></td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  name: 'Proizvod',
  data(){
    return {
      proizvodi:{
        productId: 1,
        productName: String,
        categoryId: String,
        category: null,
        unitPrice: Number,
        unitsInStock: Number
      },
      proizvod:[]
    }
  },
  methods:{
    GetProducts(){
        axios.get('http://94.156.189.137:8000/api/Products/'+this.proizvod.id)
        .then((response)=> {
          this.proizvodi = response.data;
          console.log('proizvodi: ' + JSON.stringify(this.proizvodi));
        })
        .catch(function (error){
          console.log(error);
        })
      },
  }
}

    
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #000;
  margin-top: 60px;
}
</style>
