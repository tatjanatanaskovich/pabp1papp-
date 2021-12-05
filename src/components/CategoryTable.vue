<template>
    <table>
      <CategoryRow />
    </table>
</template>

<script>
  import axios from 'axios'
  import CategoryRow from './CategoryRow.vue'

  export default {
    name:'CategoryTable',
    components:{
        CategoryRow
    },
    data(){
        return {
            category:[]
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