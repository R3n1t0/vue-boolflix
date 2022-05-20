<template>
  <div>
    <p>Titolo del film: {{movie.title}}</p>
    <p>Titolo oiginale: {{movie.original_title}}</p>
    <p>Lingua: {{movie.original_language}}</p>
    <p>Voto: {{movie.vote_average}}</p>
  </div>
</template>

<script>
export default {
  name: "CardComp",

  props:{
    movie: Object
  }
}
</script>

<style lang="scss" scoped>

</style>