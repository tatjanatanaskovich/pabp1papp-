<template>
    <p><b>Ovaj deo je komponenta ProductRow.</b></p>
    
    <table>
        <tr>
            <th>Naziv proizvoda</th>
            <th>Distributer/Dobavljač proizvoda</th>
        </tr>
    </table>
        <tr> 
            <input v-model="productCopy.productName" :disabled="!edit">  {{ supp }}
            <button v-if="edit" @click="SnimiIzmenu(productCopy.productId)">Snimi izmene</button>
            <button v-if="!edit" @click="edit=true">Izmeni</button>
            <button @click="ProductDelete(productCopy.productId)">Obrisi</button>
        </tr>
</template>

<script>

    import axios from 'axios'
    export default {
        name:'ProductRow',
        props:{
            product:Object
        },
        emits:[
            'productDeleteEvent'
        ],

        data(){
            return{
                supp:"",
                productCopy:{},
                edit:false
            }
        },

        methods:{

            SnimiIzmenu(id){
                axios
                .put(`http://94.156.189.137:8000/api/Products/${id}`,this.productCopy)
                .then(response=>{
                    console.log(response)
                    this.edit=false
                })
                .catch(err=>{
                    console.log(err)
                    // alert(`Greska:${err}`)
                })
            },
            ProductDelete(id){
                axios
                .delete(`http://94.156.189.137:8000/api/Products/${id}`)
                .then(response=>{
                    console.log(response)
                    this.$emit('productDeleteEvent',null)
                })
                .catch(err=>{
                    console.log(err)
                    // alert(`Greska:${err}`)
                })
            },

            GetSupplier(id){
                axios
                .get(`http://94.156.189.137:8000/api/Suppliers/${id}`)
                .then(response=>{
                    this.supp=response.data.companyName
                    console.log(this.supp)
                })
                .catch(err=>{
                    console.log(err)
                    // alert(`Greska:${err}`)
                })
                
            }
        },

        mounted(){
            this.GetSupplier(this.product.supplierId)
            this.productCopy=this.product
        }
    }
</script>
