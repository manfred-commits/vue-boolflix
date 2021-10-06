<template>
  <main>
    <section class="films">
      <h2>Films</h2>
      <Film class="card " v-for="(film,index) in films" :key="index" :film="film"/>
    </section>
    <section class="tv-series">
      <h2>Tv-series</h2>
      <Film class="card " v-for="(tvSerie,index) in tvSeries" :key="index+tvSerie" :film="tvSerie"/>
    </section>

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

main{
  display: flex;
  flex-wrap:wrap;
  justify-content: center;
  align-items: center;

  h2{
    color: white;
    width: 100%;
    text-align: center;
  }

  .card{
    background-color: grey;
    width: 20%;
    margin: 5px 5px;
  }
  .films,.tv-series{
    display: flex;
    width: 100%;
    flex-wrap: wrap;
    justify-content: center;
    overflow-x: hidden;



  }
  
}
</style>