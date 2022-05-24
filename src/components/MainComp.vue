<template>
<main class="container-fluid">

  <div class="movie">
    <h2 class="p-4 m-2">{{title}}</h2>
    <div class="rl-container my-3 d-flex">
      <CardComp
        v-for="card in cardList" 
        :key="card.id" 
        :cardData="card"
      />
    </div>
  </div>

</main>

</template>

<script>
import CardComp from "./CardComp.vue";

export default {
  name: "MainComp",

  components: {
    CardComp,
  },

  props:{
    cardList: Array,
    genreSelected: String,
    title: String
  },

  data(){
    return{
    
    }
  },

}   
</script>

<style lang="scss" scoped>
.movie, .series{
  width: 100%;
  background-color: #141414;
  h2{
    color: #a9a9a9;
  }
}
.rl-container{
  flex-basis: 100%;
  flex-wrap: wrap;
}

</style>