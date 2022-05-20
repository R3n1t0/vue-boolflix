<template>
  <main>
    <CardComp 
      v-for="(movie, index) in movieList" 
      :key="`movie${index}`" 
      :movie="movie"
    />
  </main>
</template>

<script>
import CardComp from "./CardComp.vue";

export default {
  name: "MainComp",

  components: { CardComp },


  props:{
    movieList: Array
  },
    
}
</script>

<style lang="scss" scoped>

</style>