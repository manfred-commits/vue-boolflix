<template>
  <section class="film-container" >
    <img :src="'https://image.tmdb.org/t/p/w342'+film.poster_path" :alt="film.title?film.title:film.name" onerror="this.src != 'https://upload.wikimedia.org/wikipedia/commons/thumb/6/61/Flag.svg/600px-Flag.svg.png'? this.src = 'https://upload.wikimedia.org/wikipedia/commons/thumb/6/61/Flag.svg/600px-Flag.svg.png' : '';">
    
    
    <div class="on-hover">

      <div ><strong>Titolo:</strong>  {{film.title?film.title:film.name}}</div>

      <div><strong>Titolo Originale:</strong> {{film.original_title?film.original_title:film.original_name}}</div>
      
      <strong>Genere:</strong>
      <div class="genres" v-for="(genre,index) in movieGenres" :key="'223'+index+genre">
        {{genre+','}}
      </div>


      <div class="container-flag"> <strong>Lingua Originale </strong> 
        <img onerror="this.src != 'https://upload.wikimedia.org/wikipedia/commons/thumb/6/61/Flag.svg/600px-Flag.svg.png'? this.src = 'https://upload.wikimedia.org/wikipedia/commons/thumb/6/61/Flag.svg/600px-Flag.svg.png' : '';" :src="'https://www.unknown.nu/flags/images/'+film.original_language+'-100'" alt="">
      </div>

      <div class="score">
        <span>Media Punteggio</span>        
        <span class="star-container">
          <i class="fas fa-star" v-for="(star,index) in 5" :key="index+star" :class="index<averageToFive(film.vote_average)? 'yellow-star':'grey-star'"></i>
          
        </span>
      </div>
      <p>
        <span>Overview:</span>
        {{film.overview}}
      </p>

      <strong>Cast:</strong>
      <div class="actors-names" v-for="(actors,index) in movieCast" :key="actors+index">
        {{actors.name||''}}
      </div>
    </div>

  </section>
</template>

<script>
import '@fortawesome/fontawesome-free/js/all.js';
import axios from 'axios'
export default {
    name:'Film',
    props:['film','gen'],
    data(){
      return{
        movieCast:[],
        movieGenres:[],
      }
    },
    methods:{
      averageToFive(averageScore){
        // console.log(averageScore);
        // console.log(Math.ceil(averageScore));
        return Math.ceil(averageScore/2);
      },
      getCredits(id){
        axios
        .get('https://api.themoviedb.org/3/movie/'+id+'/credits?api_key=5280967b1aa0fc49fbfbde5e43ea83ab&language=en-US',{
          
        })
        .then((response)=> {
          // console.log(response);
          
            this.movieCast=response.data.cast;
            if(this.movieCast.length>5){
              this.movieCast.length=5;
            }
          
        })
        .catch(error => console.log(error));
        
      },
      getGenre(){
        let container=[];
        this.film.genre_ids.forEach(filmAsGen=>{
          this.gen.forEach(genId=>{
            // console.log(genId);
            // console.log(` id of array gen ${genId.id}`);
            // console.log(` id of film ${filmGenreId}`);
  
            if(genId.id==filmAsGen){
              genId.name;
              // console.log(` content of the id to return ${containerId}`);
              container.push(genId.name);
            }
          });

        });
        this.movieGenres=container;
      }
    },
    created(){
        this.getCredits(this.film.id);
        this.getGenre();
    }

}
</script>

<style lang="scss" scoped>
.film-container:hover .on-hover{
  display: flex;
  
}
.film-container{
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  align-items: center;
  position: relative;
  margin: 10px 0;
  overflow: hidden;
  

  img:first-child{
    object-fit: cover;
    object-position: center;
    height: 100%;
    width: 100%;
  }
  .on-hover{
    display: none;
    padding: 10px;
    flex-wrap: wrap;
    align-content: flex-start;
    overflow: auto;
    position: absolute;
    background-color: rgba($color: #696969, $alpha: .9);
    color: white;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;

    .genres{
      width: 100%;
    }

    .container-flag{
      display: flex;
      flex-wrap: wrap;
      align-items: center;
      justify-content: flex-start;
      width: 100%;
      img{
        margin-left: 10px;
        height: 30px;
        width: 30px;
        object-fit: contain;

      }
    }
    .score{
      width: 100%;
      span:first-child{
        display: inline-block;
        font-weight: bold;
        width: 100%;
      }

      .star-container{
      }
    }
    p{
      span{
        font-weight: bold;
      }
      font-size: 16px;
    }
    .actors-names{
      width: 100%;
    }
    .yellow-star{
      color: gold;
    }
    .grey-star{
      color: rgb(66, 66, 66);
    }

  }
}
</style>