<template>
  <main>
    <Film/>

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
        .get('/user',{
          params: {
          ID: 12345
        }
        })
        .then(function (response) {
        console.log(response);
        })
      },
    }
}
</script>

<style lang="scss" scoped>

</style>