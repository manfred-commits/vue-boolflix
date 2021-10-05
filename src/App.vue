<template>
  <div id="app">
    <Header @input="inputTransfer"/>
    <Main :headerInput="insertedInput"/>
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
    }
  },
  methods:{
    inputTransfer(input){
      this.insertedInput=input;
    }
  }
}
</script>

<style lang="scss">
#app {
  
}
</style>
