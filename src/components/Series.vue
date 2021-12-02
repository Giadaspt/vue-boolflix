<template>
  <div class="series">
    <h5>{{title2}}</h5>
    <h6>{{titleOriginal2}}</h6>
    <img 
      v-if="image == getFlag() && gotNoFlag() !== image"
      :src="getFlag()" :alt="title">
    <h6 v-if="gotNoFlag() == image"> 
        Lingua: {{lang2}}
    </h6>
    <h6>Voto {{vote2}}</h6>
  </div>
</template>

<script>
export default {
  name: "Series",
  props:{
    title2: String,
    titleOriginal2: String,
    lang2: String,
    vote2: Number,
    id2: String,
  },

  data(){
    return {
      image: this.lang2,
    }
  },

  methods:{
   getFlag(){
      
      if (this.lang2 == 'en'){
        this.image = require('../assets/img/en.png');
      } else if (this.lang2 == 'it'){
        this.image = require('../assets/img/it.png');
      } 
      return this.image
    },

    gotNoFlag(){
      if (this.image !== 'en' || this.image !== 'it'){
        return this.lang2
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