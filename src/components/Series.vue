<template>
  <div class="series">
    <h5>{{name}}</h5>
    <h6>{{titleOriginal}}</h6>
    <img 
      v-if="image == getFlag() && gotNoFlag() !== image"
      :src="getFlag()" :alt="name">
    <h6 v-if="gotNoFlag() == image"> 
        Lingua: {{lang}}
    </h6>
    <h6>Voto {{vote}}</h6>
  </div>
</template>

<script>
export default {
  name: "Series",
  props:{
    name: String,
    titleOriginal: String,
    lang: String,
    vote: Number,
    id: String,
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
@import "../assets/style/film_series.scss";
</style>