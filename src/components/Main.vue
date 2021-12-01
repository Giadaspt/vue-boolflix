<template>
  <main class="row justify-content-center">
    <Film
    v-for="(film, index) in filmFiltered " 
    :key="index"
    :title="film.title"
    :titleOriginal="film.original_title"
    :lang="film.original_language"
    :vote="film.vote_average"
    />
  </main>
</template>

<script>
import Film from "./Film.vue"

export default {
  name: "Main",

  components:{
    Film,
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
    filmFiltered(){

      this.filmDetails.filter(film =>{
        //console.log('film',film);
        //console.log(film.title);
       this.films=[
         film.title,
         film.original_title,
         film.original_language ,
         film.vote_average ,
       ]
       console.log('films', this.films);
       
         
      })
      return this.filmDetails
    }
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