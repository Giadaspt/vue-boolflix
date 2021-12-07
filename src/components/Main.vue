<template>
  <main class="container ">
    
    <div class="row  movie">
      <h3 class="title">Film</h3>    
      <CoverMovie
      v-for="(film, index) in filmDetails " 
      :key="`film${index}`"
      :objItems = "film"
      
      />
    </div>

    <div class="row series">
      <h3 class="title">Series</h3>    
      <CoverMovie
      v-for="(serie, index) in seriesDetails " 
      :key="`serie${index}`"
      :objItems = "serie"
      />
    </div>
  </main>
</template>

<script>
import CoverMovie from "./CoverMovie.vue";

export default {
  name: "Main",

  components:{
    CoverMovie,

  },

  props:{
    filmDetails: Array,
    seriesDetails: Array,
  },

}
</script>

<style lang="scss" scoped>
@import "../assets/style/vars.scss";
@import "../assets/style/mixins.scss";

.movie, .series {
  background-color: red;
}

.title {
  margin: 32px 0;
}


</style>