<template>
  <header d-flex justify-content-between align-items-center>
    <h2>{{boolflix}}</h2>
    <div class="input-group inputFilm">
      <input 
        @keyup.13="searchFilm"
        v-model="inputOnSearch"
        type="text" 
        class="form-control" 
        placeholder="Cosa vuoi vedere?" >

      <button 
        @click="searchFilm"
        class="btn " 
        type="button"> 
        {{btn_cerca}}
      </button>
    </div>

  </header>
</template>

<script>
export default {
  name: "Header",

  data(){
    return {
      boolflix: "boolflix",
      btn_cerca: "cerca",

      inputOnSearch: "",
    }
  },

  methods:{
    searchFilm(){
      this.$emit('searchForMovie', this.inputOnSearch);
      this.$emit('searchForSeries', this.inputOnSearch);
      //console.log('input',this.inputOnSearch);
      this.inputOnSearch='';
    },
  },
}
</script>

<style lang="scss" scoped>
@import "../assets/style/vars.scss";
@import "../assets/style/mixins.scss";
@import "../assets/style/header.scss";



</style>