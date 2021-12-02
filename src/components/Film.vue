<template>
  <div class="film">
    <h5>{{title}}</h5>
    <h6>{{titleOriginal}}</h6>
    <img 
    v-if="image == getFlag() && gotNoFlag() !== image"
    :src="getFlag()" :alt="title">
    <h6 v-if="gotNoFlag() == image"> 
      Lingua: {{lang}}
    </h6>
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
    vote: Number,
  },

  data(){
    return {
      image: this.lang,
    }
  },

  methods:{
   getFlag(){
      
      if (this.lang == 'en'){
        this.image = require('../assets/img/en.png');
      } else if (this.lang == 'it'){
        this.image = require('../assets/img/it.png');
      } 
      // else if (this.lang !== 'en' && this.lang !== 'it'){
      //   this.lang = ''
      // } 
      return this.image
    },

    gotNoFlag(){
      if (this.image !== 'en' || this.image !== 'it'){
        return this.lang
      } 
    },
  },
}
</script>

<style lang="scss" scoped>
@import "../assets/style/vars.scss";
@import "../assets/style/mixins.scss";
@import "../assets/style/film.scss";


</style>