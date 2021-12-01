<template>
  <main>
   <div class="cards">
     <ul class="card" v-for="(item,index) in listaFilm" :key="index=index">

       <li>{{item.title}}</li>
       <li>{{item.original_title}}</li>
       <li>{{item.original_language}}</li>
       <li>{{item.vote_average}}</li>
       
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
    listaFilm : Array
  },
  computed:{
  
  },
  methods:{
    
  }
}  
</script>

<style lang="scss" scoped>
  main{
    width: 100%;
    min-height: 90vh;
    background-color: gray;
    .cards{
      display: flex;
      flex-wrap: wrap;
      .card{
        border: 1px solid black;
        height: 200px;
        width: 200px;
      }
    };
  };
</style>