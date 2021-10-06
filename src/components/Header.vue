<template>
  <header>
      <div class="col-left">
          <img src="https://logodownload.org/wp-content/uploads/2014/10/netflix-logo-1-1.png" alt="">
      </div>
      <div class="col-right">
          <input type="text" v-model="userInput" @keyup.enter="$emit('input',userInput)">
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
header{
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: .625rem 0;
    .col-left{
        margin-left: .625rem;
        img{
            object-fit: contain;
            height: 100%;
            width: 9.375rem;
        }
    }
    .col-right{

        input{
            margin-right: .625rem;
        }
    }
}
</style>