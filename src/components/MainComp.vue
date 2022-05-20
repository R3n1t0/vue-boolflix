<template>
  <main>
    <CardComp 
      v-for="(movie, index) in movieListFiltered" 
      :key="`movie${index}`" 
      :movie="movie"
    />
  </main>
</template>

<script>
import axios from "axios"
import CardComp from "./CardComp.vue";


export default {
  name: "MainComp",

  props:{
    movieSearched: String
  },

  components: { CardComp },

  data() {
    return {
      apiUrl: "https://api.themoviedb.org/3/search/movie",

      apiParams: {
        api_key: "e39b9201864cae31abf65f1dcac8bcab",
        language: "it-IT",
        query: ""
        },

        movieList: []
      }
    },

  mounted() {
    this.getApiUrl();
  },

  methods: {
    getApiUrl() {
      axios.get(this.apiUrl, {
      params: this.apiParams
      })
      .then(res => {
      this.movieList = res.data.results;
      console.log(this.movieList);
      });
    },

    movieSearching(movieSearched){
      this.query = movieSearched
    }

  },

  computed:{
    movieListFiltered(){
      return this.movieList.filter(this.query)
    }
  }
    
}
</script>

<style lang="scss" scoped>

</style>