<template>
<main class="container-fluid">

  <div class="movie">
    <h2 class="p-4 m-2">Film</h2>
    <div class="rl-container my-3 d-flex">
      <CardMoviesComp
        v-for="movie in movieList" 
        :key="movie.id" 
        :movie="movie"
      />
    </div>
  </div>

  <div class="series">
    <h2 class="p-3 m-2">Serie</h2>
    <div class="rl-container my-3 d-flex">
      <CardSeriesComp
        v-for="serie in seriesList" 
        :key="serie.id" 
        :serie="serie"
      />
    </div>
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
.movie, .series{
  width: 100%;
  background-color: #141414;
  h2{
    color: #a9a9a9;
  }
}
.rl-container{
  flex-basis: 100%;
  flex-wrap: wrap;
}

</style>