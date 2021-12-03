<template>
  <main>

    <div class="cards">
      <h1 v-if="listaFilm != ''" >Lista Film</h1>
      
      <div class="flip-card" v-for="(item,index) in listaFilm" :key="index">
        <div class="flip-card-inner">
          <div class="flip-card-front">
            <img  :src="`https://image.tmdb.org/t/p/w342/${item.poster_path}`" alt="immagine ">
          </div>
        <div class="flip-card-back">
        <p>
          <strong>Titolo: </strong>
          {{item.title}}
        </p>
        <p>
          <strong>Titolo originale: </strong>
          {{item.original_title}}
          </p>
        <p v-if="item.original_language=='en'" class="lingua" >
          <strong >Lingua: </strong>
          <img src="..\assets\img\en.png" alt="">
        </p>
        <p v-else-if="item.original_language=='it'" class="lingua">
          <strong >Lingua: </strong>
          <img src="..\assets\img\it.png" alt="">
        </p>
        <p v-else >
          <strong >Lingua: </strong>
          {{item.original_language}}
        </p>
        <p>
          <strong>Voto: </strong>
          <i v-for="i in stars(item.vote_average)" :key="i" class="fas fa-star"></i>
        </p>
        <p class="overview">
          <strong>Overview: </strong>
          {{item.overview}}
        </p>
        </div>
      </div>
      </div>
    </div>

    <div class="cards">
      <h1 v-if="listaSerie != ''" >lista serie</h1>

      <div class="flip-card" v-for="(item,index) in listaSerie" :key="index">
        <div class="flip-card-inner">
          <div class="flip-card-front">
            <img  :src="`https://image.tmdb.org/t/p/w342/${item.poster_path}`" alt="immagine ">
          </div>
        <div class="flip-card-back">
        <p>
          <strong>Titolo: </strong>
          {{item.name}}
        </p>
        <p>
          <strong>Titolo originale: </strong>
          {{item.original_name}}
          </p>
        <p v-if="item.original_language=='en'" class="lingua" >
          <strong >Lingua: </strong>
          <img src="..\assets\img\en.png" alt="">
        </p>
        <p v-else-if="item.original_language=='it'" class="lingua">
          <strong >Lingua: </strong>
          <img src="..\assets\img\it.png" alt="">
        </p>
        <p v-else >
          <strong >Lingua: </strong>
          {{item.original_language}}
        </p>
        <p>
          <strong>Voto: </strong>
          <i v-for="i in stars(item.vote_average)" :key="i" class="fas fa-star"></i>
        </p>
        <p class="overview">
          <strong>Overview: </strong>
          {{item.overview}}
        </p>
        </div>
      </div>
      </div>
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
  i{
    color: yellow;
  };
  main{
    width: 100%;
    min-height: 90vh;
    background-color: gray;
    .cards{
      display: flex;
      flex-wrap: wrap;
      h1{
        width: 100%;
        text-align: center;
        margin: 10px;
        
      };

      .flip-card {
        background-color: transparent;
        width: calc(100%/5 - 20px);
        height: 350px;
        margin: 10px;
        border: 1px solid #f1f1f1;
        perspective: 1000px; 
       
      };
      .flip-card-inner {
        position: relative;
        width: 100%;
        height: 100%;
        text-align: center;
        transition: transform 0.8s;
        transform-style: preserve-3d;
      };

      .flip-card:hover .flip-card-inner {
        transform: rotateY(180deg);
      };


      .flip-card-front, .flip-card-back {
        position: absolute;
        width: 100%;
        height: 100%;
        -webkit-backface-visibility: hidden; 
        backface-visibility: hidden;
      };

      .flip-card-front {
        background-color: #bbb;
        color: black;
        img{
          width: 100%;
          height: 100%;
        }
      };

      .flip-card-back {
        display: flex;
        flex-wrap: wrap;
        align-content: center;
        background-color: black;
        color: white;
        transform: rotateY(180deg);
         
        p{
          width: 100%;
          text-align: start;
          height: 50px;
          padding: 0 10px
        };
        
        .overview{
          overflow-y:auto;
          height: calc(350px - 205px );
        } ; 
        
        img{
          height:  20px;
        };
      };

    };
  };
</style>