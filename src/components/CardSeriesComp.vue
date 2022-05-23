<template>
  <div>
    <h3>Titolo della serie: {{serie.name}}</h3>
    <h4>Titolo oiginale: {{serie.original_name}}</h4>
    <p>Lingua: {{serie.original_language}}</p>
    <p>Voto: {{serie.vote_average}}</p>
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

</style>