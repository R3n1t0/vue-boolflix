<template>

<header>
  <div class="rl-container container-fluid d-flex justify-content-between align-items-center">
    <img src="../assets/img/netflix_official_logo_icon_168085.png" alt="">
    <div class="change d-flex">
      <input type="text" v-model.trim="searched" @keyup.enter="searching" placeholder="Cerca un Film">
      <select @change="searching" v-model="genreSelected" class="form-select mx-2">
        <option value="">All</option>
        <option value="movie">Movie</option>
        <option value="tv">Tv</option>
      </select>
    </div> 
  </div>
</header>

</template>

<script>
export default {
  name:"HeaderComp",

  data(){
    return{
      searched: "",
      genreSelected: ""
    }
  },

  methods:{

    searching(){
      this.$emit('searching', this.searched, this.genreSelected);
    /*   this.searched = ""; */
    }
  }
}
</script>

<style lang="scss" scoped>
header{
  height: 80px;
  background-image: linear-gradient(black,#141414);
  .rl-container{
    flex-basis: 100%;
    height: 100%;
    img{
      width: 100px;
      height: 50px;
      margin-left: 10px;
    }
    input{
      border-radius: 5px;
    }
    select{
      width: 100px;
      padding: 5px;
      border-radius: 5px;
    }
  }
}
</style>