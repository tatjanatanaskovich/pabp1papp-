<template>
    <table>
        <ProductRow v-for="p in products" :key="p.productId"
         :product="p" @productDeleteEvent="onProductDelete" />
         <select name="" id="">
             <option v-for="p in PageNumber" :key="p" :value="p">{{p+1}}</option>
         </select>
         <div v-if="add">
             <input type="text" v-model="newProduct.productName">
             <input type="checkbox" v-model="newProduct.discontinued">
             <button @click="AddProduct()">Dodaj proizvod</button>
         </div>
         <button @click="add=true">Add product</button>
    </table>
</template>
<script>
import axios from 'axios'
import ProductRow from './ProductRow.vue'
export default {
    name:'ProductTable',
    components:{
        ProductRow
    },
    data(){
        return {
            products:[],
            add:false,
            newProduct:{}
        }
    },
    methods:{
        
        AddProduct(){
            axios
            .post(`http://94.156.189.137:8000/api/Products`,this.newProduct)
            .then(response=>{
                
                console.log(response)
                this.newProduct.productId=response.data.productId
                this.products.push(this.newProduct)
                this.newProduct={}

            })
            .catch(err=>{
                console.log(err)
                // alert(`Greska:${err}`)
            })
        },
        onProductDelete(){
            this.GetProducts()
        },
        GetProducts(){
            axios
            .get(`http://94.156.189.137:8000/api/Products`)
            .then(response=>{
                this.products=response.data
                // this.products.forEach(p=>{
                //     DohvatiSupp(p.id)
                // })
                console.log(this.products)
            })
            .catch(err=>{
                console.log(err)
                // alert(`Greska:${err}`)
            })
        }
    },
    mounted(){
        this.GetProducts()
    }
}
</script>