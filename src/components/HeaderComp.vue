<template>

<header>
  <div class="rl-container container-fluid d-flex justify-content-between align-items-center">
    <img src="../assets/img/netflix_official_logo_icon_168085.png" alt="">
    <div class="change">
      <input type="text" v-model.trim="searched" @keyup.enter="searching">
<!--       <select @change="onChange" name="search" id="" class="mx-2">
        <option value="">All</option>
        <option value="Movies">Movies</option>
        <option value="Series">Series</option>
      </select> -->
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
      this.$emit('searching', this.searched);
      this.searched = "";
    }
/*     onChange(e){
      this.genreSelected = e.target.value;
      this.$emit('genreSelecting', this.genreSelected)
    } */
  }
}
</script>

<style lang="scss" scoped>
header{
  height: 80px;
  
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
      padding: 1px;
      border-radius: 5px;
    }
  }
}
</style>