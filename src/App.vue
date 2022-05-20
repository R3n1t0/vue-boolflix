<template>
  <div>
    
    <HeaderComp />

    <MainComp />

  </div>
</template>

<script>
import HeaderComp from "./components/HeaderComp.vue"
import MainComp from "./components/MainComp.vue"
import axios from "axios"
import { METHODS } from "http"

export default {
  name: 'App',

  components: {
    HeaderComp,
    MainComp
  },

  data(){
    return{
      apiUrl: "https://developers.themoviedb.org/3",
      movieList: []
    };
  },

  mounted(){
    this.getApiUrl();
  },

  methods:{
    getApiUrl(){
      axios.get(this.apiUrl)
      .then(res => {
        this.movieList = res.data
      })
    }
  }
}
</script>

<style lang="scss">

</style>
