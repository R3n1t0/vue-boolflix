<template>
  <div>
    
    <HeaderComp @movieSearching="movieSearching"/>

    <MainComp :movieList="movieList"/>

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
      apiUrl: "https://api.themoviedb.org/3/search/movie",

      apiParams: {
        api_key: "e39b9201864cae31abf65f1dcac8bcab",
        language: "it_IT",
        query: ""
      },

      movieList: [],

      movieSearched: ""
    }
  },

  methods: {
    getApi() {
      axios.get(this.apiUrl, {
      params: this.apiParams
      })
      .then(res => {
      this.movieList = res.data.results;
      console.log(this.movieList);
      });
    },

    movieSearching(movieSearched){
      
      this.apiParams.query = movieSearched
      this.getApi()
      console.log(this.apiParams.query);
    }
  }
}
</script>

<style lang="scss">
@import './assets/style/general';

</style>
