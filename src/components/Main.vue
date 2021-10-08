<template>
  <main>
    <section class="films">
      <h2>Films</h2>
      <Film class="card " v-for="(film,index) in filmFilter" :key="index" :film="film" :gen="genres"/>
    </section>
    <section class="tv-series">
      <h2>Tv-series</h2>
      <Film class="card " v-for="(tvSerie,index) in tvSeriesFilter" :key="index+tvSerie" :film="tvSerie" :gen="genres"/>
    </section>

  </main>
</template>

<script>
import Film from './Film.vue';
import axios from 'axios'

export default {
    name:'Main',
    props:['headerInput','selection'],
    data(){
      return{
        films:[],
        tvSeries:[],
        genres:[],
      }
    },
    components:{
        Film,
    },
    methods:{
   
    },
    computed:{
      filmFilter(){
        const filmFiltered = this.films.filter(
          (element)=>{
            
            if(this.selection!=""){
              return element.genre_ids.includes(this.selection);
            }
            return true;
           
          }
        );
      
      return filmFiltered;
      },
      tvSeriesFilter(){
        const tvFiltered = this.tvSeries.filter(
          (element)=>{
            
            if(this.selection!=""){
              return element.genre_ids.includes(this.selection);
            }
            return true;
          }
        );
      
      return tvFiltered;
      },
      
    },
    created(){
      axios
        .get('https://api.themoviedb.org/3/genre/movie/list?api_key=5280967b1aa0fc49fbfbde5e43ea83ab&language=en-US',{
          
        })
        .then((response)=> {
          console.log(response);
          this.genres=response.data.genres;
          this.$emit('select',this.genres);
        });
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