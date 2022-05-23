<template>
  <div>
    <h3>Titolo del film: {{movie.title}}</h3>
    <h4>Titolo oiginale: {{movie.original_title}}</h4>
    <p>Lingua: {{movie.original_language}}</p>
    <p>Voto: {{movie.vote_average}}</p>
  </div>
</template>

<script>
export default {
  name: "CardMoviesComp",

  props:{
    movie: Object
  }
}
</script>

<style lang="scss" scoped>

</style>