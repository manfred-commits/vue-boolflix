<template>
  <section class="film-container" >
    <!-- <img :src="'https://image.tmdb.org/t/p/w500'+film.backdrop_path" :alt="film.title"> -->
    <h4>Titolo:{{film.title}}</h4>
    <h4>Titolo Originale:{{film.original_title}}</h4>
    <div>Lingua Originale:{{film.original_language}}</div>
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