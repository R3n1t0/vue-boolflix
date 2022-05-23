<template>
  <main class="container">

    <h2>Film</h2>
    <CardMoviesComp
      v-show="moviesShow" 
      v-for="movie in movieList" 
      :key="movie.id" 
      :movie="movie"
    />

    <h2>Serie</h2>
    <CardSeriesComp 
      v-show="seriesShow"
      v-for="serie in seriesList" 
      :key="serie.id" 
      :serie="serie"
    />

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
      movies: true,
      series: true
    }
  },

  methods:{
    moviesShow(){
      if(this.genreSelected === "" || this.genreSelected === "Movie") this.movies = true;
      else this.movies = false;
      console.log(this.movies);

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