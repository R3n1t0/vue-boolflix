<template>
  <div>
    
    <HeaderComp @movieSearching="movieSearching"/>

    <MainComp :movieSearched="movieSearched"/>

  </div>
</template>

<script>
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
      movieSearched: ""
    }
  },

  methods:{
    movieSearching(movieSearched){
      this.movieSearched = movieSearched
      console.log(movieSearched);
    }
  }

}
</script>

<style lang="scss">
@import './assets/style/general';

</style>
