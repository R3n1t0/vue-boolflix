<template>
  <div>
    <div v-if="!error">
      <HeaderComp @searching="searching"/>

      <MainComp :movieList="movieList" :seriesList="seriesList" :genreSelected="genreSelected"/>
    </div>

    <div v-else>
      <h1>Errore: Indirizzo sbagliato</h1>
    </div>

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
      genreSelected: "",
      error: false
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
      })
      .catch((error) => {
        console.log(error);
        this.error = true
      })
    },

    searching(searched){
      this.apiParams.query = searched
      this.getMovieApi();
      this.getSeriesApi()
    },

/*     genreSelecting(genreSelected){
      this.genreSelected = genreSelected
    } */
  }
}
</script>

<style lang="scss">
@import './assets/style/general';

</style>
