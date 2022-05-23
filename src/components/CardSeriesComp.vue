<template>
  <div class="rl-card p-2">

    <div class="card-inner">
      <div class="card-front">
        <img :src="`http://image.tmdb.org/t/p/w342/${serie.poster_path}`" :alt="serie.name">
      </div>

      <div class="card-back p-2">
        <h3>Titolo della serie: {{serie.name}}</h3>
        <h4>Titolo oiginale: {{serie.original_name}}</h4>
        <p>Lingua: {{serie.original_language}}</p>
        <p>Voto: {{serie.vote_average}}</p>
      </div>
    </div>

  </div>
</template>

<script>
export default {
  name: "CardSeriesComp",

  props:{
    serie: Object
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
    }
  }
}
.rl-card:hover .card-inner {
  transform: rotateY(180deg);
}

</style>