<template>
  <header>

    <div class="logo"><h2>Boolflix</h2></div>

    <div class="input">
      <input type="text" v-model="value">
      <button @click="$emit('searchFilm',value)" >invia</button>
    </div>

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
    background: linear-gradient(black ,gray);
    display: flex;
    justify-content: space-between;
    align-items: center;
    .logo , .input{
      margin: 0 10px;
    };
    .logo{
      h2{
        color: rgb(192, 5, 5)
      };
    };
  };
</style>