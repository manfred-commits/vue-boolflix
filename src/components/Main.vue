<template>
  <main>
    <Film/>

  </main>
</template>

<script>
import Film from './Film.vue';

export default {
    name:'Main',
    props:['headerInput'],
    components:{
        Film,
    }
}
</script>

<style lang="scss" scoped>

</style>