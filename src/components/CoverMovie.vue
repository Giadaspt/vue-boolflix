<template>
  <div class="col d-flex justify-content-center flex-wrap" >

    <div class="flip-card film">
      <div class="flip-card-inner">
        <div class="flip-card-front">
          <img :src="getPoster()" alt="">
        </div>
        <div class="flip-card-back">
          <h5>{{title}}</h5>
          <h6>{{titleOriginal}}</h6>
          <p>{{overview}}</p>
          <img 
          class="flag"
          v-if="image == getFlag() && gotNoFlag() !== image"
          :src="getFlag()" :alt="title">
          <h6 v-if="gotNoFlag() == image"> 
            Lingua: {{lang}}
          </h6>
          <h6>Voto {{vote}}</h6>
        </div>
      </div>
    </div>

 
  </div>
</template>

<script>
export default {
  name: "CoverMovie",

  props:{
    title: String,
    titleOriginal: String,
    lang: String,
    vote: Number,
    id: Number,
    overview: String,
    preview: String,
  },

  data(){
    return {
      image: this.lang,
      base: 'https://image.tmdb.org/t/p/w342',
    }
  },

  methods:{
   getFlag(){
      
      if (this.lang == 'en'){
        this.image = require('../assets/img/en.png');
      } else if (this.lang == 'it'){
        this.image = require('../assets/img/it.png');
      } 
      return this.image
    },

    gotNoFlag(){
      if (this.image !== 'en' || this.image !== 'it'){
        return this.lang
      }
    },

    getPoster() {
      return this.base+this.preview;
    },

    starCount(item) {
      return Math.ceil(item.vote_average / 2);
    },
  },
}
</script>

<style lang="scss" scoped>
@import "../assets/style/vars.scss";
@import "../assets/style/mixins.scss";
@import "../assets/style/film_series.scss";


</style>