<template>
  <div>
    <div v-if="!error">
      <HeaderComp @searching="searching"/>

      <MainComp v-if="movie.length > 0" title="Film" :cardList="movie"/>
      <MainComp v-if="tv.length > 0" title="Serie Tv" :cardList="tv"/>

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
      apiMovieUrl: "https://api.themoviedb.org/3/search/",

      apiParams: {
        api_key: "e39b9201864cae31abf65f1dcac8bcab",
        language: "it_IT",
        query: ""
      },

      movie: [],
      tv: [],

      searched: "",
      genreSelected: "",
      error: false
    }
  },

  methods:{
     searching(searched, genreSelected){
      this.movie = [];
      this.tv = [];
      this.apiParams.query = searched
      if(searched.length > 0){
        if(genreSelected === ""){
          this.getApi("movie"); 
          this.getApi("tv");
        }else{
          this.getApi(genreSelected)
        }  
      } 
    },

    getApi(type) {
      axios.get(this.apiMovieUrl + type, {
      params: this.apiParams
      })
      .then(res => {
      this[type] = res.data.results;
      })
      .catch((error) => {
        console.log(error);
        this.error = true
      })
    },

  }
}
</script>

<style lang="scss">
@import './assets/style/general';

</style>
