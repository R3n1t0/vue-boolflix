<template>
<main class="container-fluid">

  <h2 class="m-3">Film</h2>
  <div class="rl-container my-3 d-flex">
    <CardMoviesComp
      v-for="movie in movieList" 
      :key="movie.id" 
      :movie="movie"
    />
  </div>

  <h2 class="m-3">Serie</h2>
  <div class="rl-container my-3 d-flex">
    <CardSeriesComp
      v-for="serie in seriesList" 
      :key="serie.id" 
      :serie="serie"
    />
  </div>

</main>

</template>

<script>
import CardMoviesComp from "./CardMoviesComp.vue";
import CardSeriesComp from "./CardSeriesComp.vue";


export default {
  name: "MainComp",

  components: {
    CardMoviesComp,
    CardSeriesComp
  },

  props:{
    movieList: Array,
    seriesList: Array,
    genreSelected: String
  },

  data(){
    return{
    
    }
  },

}   
</script>

<style lang="scss" scoped>
main{
  background-color: #141414;
  .rl-container{
    flex-basis: 100%;
    flex-wrap: wrap;
  }
}

</style>