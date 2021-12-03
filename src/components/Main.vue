<template>
  <main>

   <div class="cards">
     <h1 v-if="listaFilm != ''" >lista film</h1>
     <ul class="card" v-for="(item,index) in listaFilm" :key="index=index">
       <img  :src="`https://image.tmdb.org/t/p/w342/${item.backdrop_path}`" alt="immagine assente">
       <li>{{item.title}}</li>
       <li>{{item.original_title}}</li>
       <li v-if="item.original_language=='en'" ><img src="..\assets\img\en.png" alt=""></li>
       <li v-if="item.original_language=='it'" ><img src="..\assets\img\it.png" alt=""></li>
       <li v-else >{{item.original_language}}</li>
       <i v-for="i in stars(item.vote_average)" :key="i=i" class="fas fa-star"></i>
       
     </ul>
   </div>

   <div class="cards">
     <h1 v-if="listaSerie != ''" >lista serie</h1>
     <ul class="card" v-for="(item,index) in listaSerie" :key="index=index">
       <img  :src="`https://image.tmdb.org/t/p/w342/${item.backdrop_path}`" alt="immagine assente">
       <li>{{item.name}}</li>
       <li>{{item.original_name}}</li>
       <li v-if="item.original_language=='en'" ><img src="..\assets\img\en.png" alt=""></li>
       <li v-if="item.original_language=='it'" ><img src="..\assets\img\it.png" alt=""></li>
       <li v-else >{{item.original_language}}</li>
       <i v-for="i in stars(item.vote_average)" :key="i=i" class="fas fa-star"></i>
     </ul>
   </div>

  </main>
</template>

<script>


export default {
  name:'Main',

  data(){
    return{
      
      }
  },

  props:{
    listaFilm : Array,
    listaSerie : Array
  },
  computed:{
    
    },
  methods:{
    stars(value){
      const stars = Math.floor(value/2)+1 ;
      return stars
    }
    }
}  
</script>

<style lang="scss" scoped>
  @import '~@fortawesome/fontawesome-free/css/all.min.css';
  
  main{
    width: 100%;
    min-height: 90vh;
    background-color: gray;
    .cards{
      display: flex;
      flex-wrap: wrap;
      h1{
        width: 100%;
      }
      .card{
        border: 1px solid black;
        min-height: 200px;
        width: 200px;
        list-style-type:  none;
        img{
          width: 200px;
        };
        li{
          img{
           width: 30px;
          };
        };
      };
    };
  };
</style>