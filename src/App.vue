<template>
  <div id="app">
    <Header @input="inputTransfer" :genres="transferedGen" @current="getCurrentSelect"/>
    <Main :headerInput="insertedInput" @select="getGenres" :selection="selected"/>
  </div>
</template>

<script>
import Header from './components/Header.vue';
import Main from './components/Main.vue';

export default {
  name: 'App',
  
  components: {
    Header,
    Main
  },
  data(){
    return{
      insertedInput:"",
      transferedGen:[],
      selected:"",
    }
  },
  methods:{
    inputTransfer(input){
      this.insertedInput=input;
    },
    getGenres(genresForSelect){
      this.transferedGen=genresForSelect;
    },
    getCurrentSelect(genresSelected){
      this.selected=genresSelected;
    }
  }
}
</script>

<style lang="scss">
@import './assets/style/common.scss';
#app {
  
}
</style>
