<template>
  <div class="film">
    <h5>{{title}}</h5>
    <h6>{{titleOriginal}}</h6>
    <img 
    v-if="image == getFlag()"
    :src="getFlag()" :alt="title">
    <h6
    v-else
    >Lingua: {{getFlag}}</h6>
    <h6>Voto {{vote}}</h6>
  
  </div>
</template>

<script>
export default {
  name: "Film",

  props:{
    title: String,
    titleOriginal: String,
    lang: String,
    backimage: Image,
    vote: Number,
  },

  data(){
    return {
      image: this.lang,
      backImage: this.backimage,
    }
  },

  methods:{
   getFlag(){
      console.log('lang',this.image);
      if (this.lang == 'en'){
        this.image = require('../assets/img/en.png');
      } else if (this.lang == 'it'){
        this.image = require('../assets/img/it.png');
      } else {
        this.backImage 
        console.log('backimage',this.backImage);
      }
      return this.image
    },
  },
}
</script>

<style lang="scss" scoped>
@import "../assets/style/vars.scss";
@import "../assets/style/mixins.scss";
@import "../assets/style/film.scss";


</style>