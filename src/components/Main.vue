<template>
  <main class="container ">
        
    <h3 class="title">Film</h3>
    <div class="row  movie">
      <i class="fas fa-chevron-left leftChev"></i>
      <CoverMovie
        v-for="(film, index) in filmDetails " 
        :key="`film${index}`"
        :objItems = "film"/>
        <i class="fas fa-chevron-right rightChev"></i>
    </div>

    <h3 class="title">Series</h3> 
    <div class="row series">
      <i class="fas fa-chevron-left leftChev"></i>   
      <CoverMovie
        v-for="(serie, index) in seriesDetails " 
        :key="`serie${index}`"
        :objItems = "serie"/>
        <i class="fas fa-chevron-right rightChev"></i>
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

  data(){
    return {
      show: false,
      index: -1,
    }
  },

  method:{
    slideScroll(){

    }
  }

}
</script>

<style lang="scss" scoped>
@import "../assets/style/vars.scss";
@import "../assets/style/mixins.scss";
@import "../assets/style/main.scss";

</style>