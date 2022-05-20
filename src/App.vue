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
        api_key:"e39b9201864cae31abf65f1dcac8bcab",
        language: "it-IT",
        query: "kill bill"
      },
      movieList: []
    };
  },

  mounted(){
    this.getApiUrl();
  },

  methods:{
    getApiUrl(){
      axios.get(this.apiUrl, {
        params: this.apiParams
      })
      .then(res => {
        console.log(res);
      })
    }
  }
}
</script>

<style lang="scss">
@import './assets/style/general';

</style>
