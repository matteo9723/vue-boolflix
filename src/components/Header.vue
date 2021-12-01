<template>
  <header>
    <input type="text" v-model="value">
    <button @click="$emit('searchFilm',value)" >invia</button>
  </header>
</template>

<script>

export default {

  data(){
    return{
      value:''
    }
  },

  methods:{
  
  }

}


</script>

<style lang="scss" scoped>
  header{
    width: 100%;
    height: 10vh;
    background-color: red
  };
</style>