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
          <img 
          class="flag"
          v-if="image == getFlag() && gotNoFlag() !== image"
          :src="getFlag()" :alt="title">
          <h6 v-if="gotNoFlag() == image"> 
            Lingua: {{lang}}
          </h6>

          <div>
            <i 
            v-for="i in 5" :key="i" 
            :class="i < stars(vote) ? 'fas fa-star' : 'far fa-star'"></i>
          </div>

           <p class="overview">{{textCut(overview)}}...</p>

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
      cutText: this.overview,
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

    stars(item) {
      return Math.ceil(item.vote_average / 2);
    },

    textCut(){
      return this.cutText.slice(0,220)
    }
  },
}
</script>

<style lang="scss" scoped>
@import "../assets/style/vars.scss";
@import "../assets/style/mixins.scss";
@import "../assets/style/film_series.scss";


</style>