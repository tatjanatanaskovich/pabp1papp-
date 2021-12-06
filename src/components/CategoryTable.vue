<template>
  <p><b>Ovaj deo je komponenta CategoryTable.</b></p>
    <table>
      <Category />
    </table>
</template>

<script>
  import axios from 'axios'
  import Category from './Category.vue'

  export default {
    name:'CategoryTable',
    components:{
      Category
    },
    data(){
      return {
        categories: [],
      }
    },
    methods:{

      GetCategories(){
        axios
          .get(`http://94.156.189.137:8000/api/Categories`)
          .then((response)=>{
            this.categories=response.data;
            console.log(this.category);
            })
          .catch(function (error){
            console.log(error);
          })
      }

    },

    mounted(){
        this.GetCategories();
    }
  }
</script>