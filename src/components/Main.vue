<template>
  <main class="container  justify-content-center">
    <div class="row d-flex justify-content-center">
    <h3>Film</h3>    
    <CoverMovie
    v-for="film in filmDetails " 
    :key="film.id"
    :preview="film.poster_path"
    :title="film.title"
    :titleOriginal="film.original_title"
    :overview="film.overview"
    :lang="film.original_language"
    :vote="film.vote_average"
    />
    </div>
    <div class="row d-flex justify-content-center">
    <h3>Series</h3>    
    <CoverMovie
    v-for="serie in seriesDetails " 
    :key="serie.id2"
    :toSee="serie.CoverMovie"
    :preview="serie.poster_path"
    :name="serie.name"
    :titleOriginal="serie.original_title"
    :overview="serie.overview"
    :lang="serie.original_language"
    :vote="serie.vote_average"
    />
    </div>

  </main>
</template>

<script>
import CoverMovie from "./CoverMovie.vue"

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
      textInput: '',
    }
  },

  computed:{
  },

  methods:{

  },

}
</script>

<style lang="scss" scoped>
@import "../assets/style/vars.scss";
@import "../assets/style/mixins.scss";

.row {
  overflow: hidden;
  margin: 32px;
}


</style>