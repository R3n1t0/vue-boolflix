<template>
  <div class="rl-card p-2">

    <div class="card-inner">
      <div class="card-front">
        <img :src="`http://image.tmdb.org/t/p/w342/${cardData.poster_path}`" :alt="cardData.title">
      </div>

      <div class="card-back p-2">
        <h3>Titolo del film: {{cardData.title || cardData.name}}</h3>
        <h4>Titolo oiginale: {{cardData.original_title || cardData.original_name}}</h4>
        <img v-if="flags.includes(cardData.original_language)" :src="require(`../assets/img/${cardData.original_language}.png`)" alt="">
        <p v-else>Lingua: {{cardData.original_language}}</p>
        <p>Voto: {{Math.round(cardData.vote_average)/2}}</p>

        <i 
          v-for="i in Math.floor(Math.round(cardData.vote_average)/2)"
          :key="`a${i}`"
          class="fa-star fa-solid"></i>

        <i v-if="Math.round(cardData.vote_average) % 2" class="fa-solid fa-star-half-stroke"></i> 
              
        <i 
          v-for="i in (5 - Math.floor(Math.round(cardData.vote_average)/2) - (Math.round(cardData.vote_average) % 2) )"
          :key="`b${i}`"
          class="fa-star fa-regular">
        </i>

        <p class="description">
          {{cardData.overview}}
        </p>
      </div>
    </div>

  </div>
</template>

<script>
export default {
  name: "CardComp",

  data(){
    return{
      flags: ["it", "en"]
    }
  },

  props:{
    cardData: Object
  }
}
</script>

<style lang="scss" scoped>
.rl-card{
  width: 20%;
  height: 350px;
  background-color: transparent;
  perspective: 1000px;
  .card-inner {
    position: relative;
    width: 100%;
    height: 100%;
    text-align: center;
    transition: transform 0.8s;
    transform-style: preserve-3d;
    box-shadow: 0 4px 8px 0 rgba(0,0,0,0.2);
    .card-front, .card-back {
      position: absolute;
      width: 100%;
      height: 100%;
      -webkit-backface-visibility: hidden;
      backface-visibility: hidden;
      
      img{
        width: 100%;
        height: 100%;
      }
    }
    .card-back {
      background-color: transparent;
      color: white;
      transform: rotateY(180deg);
      img{
        width: 30px;
        height: 30px;
        padding: 5px;
      }
      .description{
      height: 50%;
      overflow-y: auto;
      }
    }
  }
}
.rl-card:hover .card-inner {
  transform: rotateY(180deg);
}
</style>