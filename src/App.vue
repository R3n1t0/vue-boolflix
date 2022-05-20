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
        console.log(res);
      })
    }
  }
}
</script>

<style lang="scss">
@import './assets/style/general';

</style>
