<template>
  <main class="row justify-content-center">
    <Film
    v-for="(film, index) in filmDetails" 
    :key="index"
    :title="filmDetails.title"
    :titleOriginal="filmDetails.original_title"
    :lang="filmDetails.original_language"
    :vote="filmDetails.vote_average"
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
    filmDetails: Object,
  },

  data(){
    return {
      textInput: '',
    }
  },

  computed:{
    filmFiltered(){

      this.filmDetails.filter(film =>{
        console.log('film',film);
      })
      console.log('film det', this.filmDetails);
      return ''
    }
  },


}
</script>

<style lang="scss" scoped>
@import "../assets/style/vars.scss";
@import "../assets/style/mixins.scss";
@import "../assets/style/main.scss";


</style>