<template>
  <main class="container  justify-content-center">
    <div class="row d-flex justify-content-center">
    <h3>Film</h3>    
    <Film
    v-for="film in filmDetails " 
    :key="film.id"
    :title="film.title"
    :titleOriginal="film.original_title"
    :lang="film.original_language"

    :vote="film.vote_average"
    />
    </div>

    <div class="row d-flex justify-content-center">
    <h3>Series</h3>    
    <Series
    v-for="serie in seriesDetails " 
    :key="serie.id2"
    :name="serie.name"
    :titleOriginal="serie.original_title"
    :lang="serie.original_language"
    :vote="serie.vote_average"
    />
    </div>

  </main>
</template>

<script>
import Film from "./Film.vue"
import Series from "./Series.vue"

export default {
  name: "Main",

  components:{
    Film,
    Series,
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
@import "../assets/style/main.scss";


</style>