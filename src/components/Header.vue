<template>
  <header>
      <div class="col-left">
          <h1>Boolflix</h1>
      </div>
      <div class="col-right">
          <select v-if="counter!=0" v-model="currentGenre" @change="$emit('current',currentGenre)" name="genres" id="genres">
              <option value="">Inserisci un genere</option>
              <option v-for="(genre,index) in genres" :key="genre+index+'2'" :value="genre.id">{{genre.name}}</option>

          </select>
          <input placeholder="Inserisci un film/una serie tv" type="text" v-model="userInput" @keyup.enter="$emit('input',userInput)&& counter++ ">
      </div>
  </header>
</template>

<script>


export default {
    name:'Header',
    props:['genres'],
    data(){
        return{
            userInput:"",
            currentGenre:"",
            counter:""
        }
    }
}
</script>

<style lang="scss" scoped>
header{
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: .625rem 0;
    background-color: rgb(37, 37, 37);
    h1{
        color: red;
    }
    .col-left{
        margin-left: .625rem;
        img{
            object-fit: contain;
            height: 100%;
            width: 9.375rem;
        }
    }
    .col-right{
        display: flex;
        justify-content: flex-end;
        align-items: center;
        height: 100%;
        width: 40%;

    select,input{
            height: 40px;
            width: 50%;
            margin-right: .625rem;
        }
    }
}
</style>