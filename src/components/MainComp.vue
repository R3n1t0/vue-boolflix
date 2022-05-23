<template>
  <main class="container">

    <CardMovieComp
      v-show="movieShow" 
      v-for="movie in movieList" 
      :key="movie.id" 
      :movie="movie"
    />

    <CardSeriesComp 
      v-show="seriesShow"
      v-for="serie in seriesList" 
      :key="serie.id" 
      :serie="serie"
    />

  </main>
</template>

<script>
import CardMovieComp from "./CardMovieComp.vue";
import CardSeriesComp from "./CardSeriesComp.vue";

export default {
  name: "MainComp",

  components: {
    CardMovieComp,
    CardSeriesComp
  },

  props:{
    movieList: Array,
    seriesList: Array,
    genreSelected: String
  },

  data(){
    return{
      movies: true,
      series: true
    }
  },

  methods:{
    movieShow(){
      if(this.genreSelected === "" || this.genreSelected === "Movie") this.movies = true;
      else this.movies = false;
      return this.movies
    },

    seriesShow(){
      if(this.genreSelected === "" || this.genreSelected === "Series") this.movies = true;
      else this.movies = false;
      return this.movies
    } 
  }
    
}
</script>

<style lang="scss" scoped>

</style>