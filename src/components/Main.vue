<template>
  <main>
    <Film v-for="(film,index) in films" :key="index" :film="film"/>

  </main>
</template>

<script>
import Film from './Film.vue';
import axios from 'axios'

export default {
    name:'Main',
    props:['headerInput'],
    data(){
      return{
        films:[],
      }
    },
    components:{
        Film,
    },
    methods:{
   
    },
    watch:{
      headerInput:function(){
        axios
        .get('https://api.themoviedb.org/3/search/movie',{
          params: {
          api_key: '5280967b1aa0fc49fbfbde5e43ea83ab',
          query:this.headerInput,
        }
        })
        .then((response)=> {
        console.log(response.data.results);
        this.films=response.data.results;
        })
      },
    }
}
</script>

<style lang="scss" scoped>

</style>