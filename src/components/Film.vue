<template>
  <section class="film-container" >
    <img src="" alt="">
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