<template>
  <section class="film-container" >
    <!-- <img :src="'https://image.tmdb.org/t/p/w500'+film.backdrop_path" :alt="film.title"> -->
    <h4 >Titolo:{{film.title?film.title:film.name}}</h4>
    <h4>Titolo Originale:{{film.original_title?film.original_title:film.original_name}}</h4>
    <div>Lingua Originale:
      <img onerror="this.src != 'https://upload.wikimedia.org/wikipedia/commons/thumb/6/61/Flag.svg/600px-Flag.svg.png'? this.src = 'https://upload.wikimedia.org/wikipedia/commons/thumb/6/61/Flag.svg/600px-Flag.svg.png' : '';" :src="'https://www.unknown.nu/flags/images/'+film.original_language+'-100'" alt="">
    </div>
    <div class="score">Media Punteggio:{{film.vote_average}}</div>
  </section>
</template>

<script>
export default {
    name:'Film',
    props:['film'],

}
</script>

<style lang="scss" scoped>

</style>