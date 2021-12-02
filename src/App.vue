<template>
  <div id="app">
    <Header @searchFilm="ricerca" />
    <Main :listaFilm="listaFilm" :listaSerie="listaSerie" />
  </div>
</template>

<script>

import Header from './components/Header.vue'
import Main from './components/Main.vue'
import axios from 'axios'

export default {
  name: 'App',
  components: {
    Main,
    Header
  },

  data(){
    return{ 
      listaFilm:[],
      listaSerie:[]
    }
  },

  methods:{
    ricerca(value){
     
      axios.get(`https://api.themoviedb.org/3/search/movie?api_key=9f9a8bc474e9c025cefdaf1ff2c51e03&query=${value}`).then( r =>{
        this.listaFilm=r.data.results
        console.log(r.data.results);
      }).catch( e => {
       console.log(e);
      });
      axios.get(`https://api.themoviedb.org/3/search/tv?api_key=9f9a8bc474e9c025cefdaf1ff2c51e03&query=${value}`).then( r =>{
        this.listaSerie=r.data.results
      }).catch( e => {
       console.log(e);
      });
     
    }
  }


}
</script>

<style lang="scss">
  *{
    box-sizing: border-box;
    margin: 0;
    padding: 0;
  }
</style>
