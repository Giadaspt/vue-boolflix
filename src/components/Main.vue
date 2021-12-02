<template>
  <main >
    <div class="row justify-content-center">
    <h3>Film</h3>    
    <Film
    v-for="(film, index) in filmDetails " 
    :key="index"
    :title="film.title"
    :titleOriginal="film.original_title"
    :lang="film.original_language"
    :backimage="film.backdrop_path"
    :vote="film.vote_average"
    />
    </div>
    <div class="row justify-content-center">
    <h3>Series</h3>    
    <Series/>
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
  },

  data(){
    return {
      textInput: '',
      films: [],
    }
  },

  computed:{
  },

  methods:{
    getFilmsIndex(index){
      this.indexFilm = index
      console.log(this.indexFilm);
      console.log(index);
    }
  },


}
</script>

<style lang="scss" scoped>
@import "../assets/style/vars.scss";
@import "../assets/style/mixins.scss";
@import "../assets/style/main.scss";


</style>