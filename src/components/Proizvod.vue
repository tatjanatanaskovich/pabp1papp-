<template>
  <div>
    <h2>Unos proizvoda</h2>
    <div id="unos_proizvoda">
      <div>
        <label for="">Naziv proizvoda </label>
        <input type="text" v-model="proizvod.naziv">
      </div>
      <div>
        <label for="">Cena proizvoda </label>
        <input type="number" v-model="proizvod.cena">
      </div>
      <div>
        <label for="">Količina proizvoda </label>
        <input type="number" v-model="proizvod.kolicina">
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
          <td></td>
        </th>
        <tbody>
          <tr  v-for="(p,index) in proizvodi" :key="p">
            <td>{{ p.naziv }}</td>
            <td>{{ p.kolicina }}</td>
            <td>{{ p.cena }}</td>
            <td><button @click="IzmeniProizvod(index)">Izmeni proizvod</button></td>
            <td><button @click="ObrisiProizvod(index)">Obriši proizvod</button></td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Proizvod',
  data(){
    return {
      proizvod:{},
      proizvodi:[]
    }
  },
  methods:{
    UnesiProizvod(){
      this.proizvod.naziv=this.proizvod.naziv.trim();
      this.proizvod.cena=parseInt(this.proizvod.cena);
      this.proizvod.kolicina=parseInt(this.proizvod.kolicina);
      this.proizvodi.push(this.proizvod);
      this.proizvod={}
    },
    IzmeniProizvod(rb){
      this.proizvodi.push({
        index:rb,
        kolicina:1
      });
    },
    ObrisiProizvod(rb){
      this.proizvodi.pop({
        index:rb,
        kolicina:1
      });
    }
  },
  computed:{
    ProveriUnos(){
      if(Number.isNaN(parseInt(this.proizvod.cena)) || Number.isNaN(parseInt(this.proizvod.kolicina))){
        return true;
      }
      return false;
    },
   
    ProveriKolicinu(){
      return function(artikal){
        if(artikal.kolicina>this.proizvodi[artikal.index].kolicina){
          return "background-color:#F08080";
        }
        return "";
      }
    }
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
