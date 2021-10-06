<template>
  <section class="film-container" >
    <img :src="'https://image.tmdb.org/t/p/w500'+film.backdrop_path" :alt="film.title?film.title:film.name" onerror="this.src != 'https://upload.wikimedia.org/wikipedia/commons/thumb/6/61/Flag.svg/600px-Flag.svg.png'? this.src = 'https://upload.wikimedia.org/wikipedia/commons/thumb/6/61/Flag.svg/600px-Flag.svg.png' : '';">
    <h4 >Titolo:{{film.title?film.title:film.name}}</h4>
    <h4>Titolo Originale:{{film.original_title?film.original_title:film.original_name}}</h4>
    <div>Lingua Originale:
      <img onerror="this.src != 'https://upload.wikimedia.org/wikipedia/commons/thumb/6/61/Flag.svg/600px-Flag.svg.png'? this.src = 'https://upload.wikimedia.org/wikipedia/commons/thumb/6/61/Flag.svg/600px-Flag.svg.png' : '';" :src="'https://www.unknown.nu/flags/images/'+film.original_language+'-100'" alt="">
    </div>
    <div class="score">
      Media Punteggio:{{averageToFive(film.vote_average)}}
      <span>
        <i class="fas fa-star" v-for="(star,index) in stars" :key="index+star" :class="index<averageToFive(film.vote_average)? 'yellow-star':'grey-star'"></i>
        
      </span>
    </div>
  </section>
</template>

<script>
import '@fortawesome/fontawesome-free/js/all.js';
export default {
    name:'Film',
    props:['film'],
    data(){
      return{
        stars:['','','','',''],
      }
    },
    methods:{
      averageToFive(averageScore){
        console.log(averageScore);
        console.log(Math.ceil(averageScore));
        return Math.ceil(averageScore/2);
      },
      
    }

}
</script>

<style lang="scss" scoped>
.yellow-star{
  color: gold;
}
.grey-star{
  color: grey;
}
</style>