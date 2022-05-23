<template>
  <div>
    
    <HeaderComp @searching="searching" @genreSelecting="genreSelecting"/>

    <MainComp :movieList="movieList" :seriesList="seriesList" :genreSelected="genreSelected"/>

  </div>
</template>

<script>
import axios from "axios"
import HeaderComp from "./components/HeaderComp.vue"
import MainComp from "./components/MainComp.vue"

export default {
  name: 'App',

  components: {
    HeaderComp,
    MainComp
  },

  data(){
    return{
      apiMovieUrl: "https://api.themoviedb.org/3/search/movie",
      apiSeriesUrl: "https://api.themoviedb.org/3/search/tv",

      apiParams: {
        api_key: "e39b9201864cae31abf65f1dcac8bcab",
        language: "it_IT",
        query: ""
      },

      movieList: [],
      seriesList: [],

      searched: "",
      genreSelected: ""
    }
  },

  methods:{
    getMovieApi() {
      axios.get(this.apiMovieUrl, {
      params: this.apiParams
      })
      .then(res => {
      this.movieList = res.data.results;
      });
    },

    getSeriesApi() {
      axios.get(this.apiSeriesUrl, {
      params: this.apiParams
      })
      .then(res => {
      this.seriesList = res.data.results;
      });
    },

    searching(searched){
      this.apiParams.query = searched
      this.getMovieApi();
      this.getSeriesApi()
    },

    genreSelecting(genreSelected){
      this.genreSelected = genreSelected
    }
  }
}
</script>

<style lang="scss">
@import './assets/style/general';

</style>
