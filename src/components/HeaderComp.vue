<template>

<div>
  <div class="container-fluid d-flex justify-content-between align-items-center">
    <h4>logo</h4>
    <div class="change">
      <input type="text" v-model.trim="movieSearched" @keyup.enter="$emit('movieSearching', movieSearched)">
      <select v-model.trim="genreSelected" @change="$emit('genreSelecting', genreSelected)" name="search" id="" class="mx-2">
        <option value=""></option>
      </select>
    </div> 
  </div>
</div>

</template>

<script>
export default {
  name:"HeaderComp",

  data(){
    return{
      movieSearched: "",
      genreSelected: ""
    }
  }
}
</script>

<style lang="scss" scoped>

</style>