<template>
  <header>
      <div class="col-left">
          <img src="" alt="">
      </div>
      <div class="col-right">
          <input type="text" v-model="userInput">
          <button @click="$emit('input',userInput)">Invio</button>
      </div>
  </header>
</template>

<script>


export default {
    name:'Header',
    data(){
        return{
            userInput:"",
        }
    }
}
</script>

<style lang="scss" scoped>

</style>