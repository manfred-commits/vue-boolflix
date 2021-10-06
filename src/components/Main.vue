<template>
  <main>
    <Film v-for="(film,index) in films" :key="index" :film="film"/>
    <Film v-for="(tvSerie,index) in tvSeries" :key="index+tvSerie" :film="tvSerie"/>

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
        tvSeries:[]
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
        axios
        .get('https://api.themoviedb.org/3/search/tv',{
          params: {
          api_key: '5280967b1aa0fc49fbfbde5e43ea83ab',
          query:this.headerInput,
        }
        })
        .then((response)=> {
        console.log(response.data.results);
        this.tvSeries=response.data.results;
        })
        
      },
    }
}
</script>

<style lang="scss" scoped>

</style>