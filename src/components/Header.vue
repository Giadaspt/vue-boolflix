<template>
  <header d-flex justify-content-between align-items-center>
    <h2>{{boolflix}}</h2>
    <div class="input-group inputFilm">
      <input 
        v-model="inputOnSearch"
        type="text" 
        class="form-control" 
        placeholder="Cerca un film" >

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
    searchFilm(text){
      this.$emit('searchForMovie', this.inputOnSearch)
      console.log('parametro funct',text);
      console.log('input',this.inputOnSearch);
    }
  },
}
</script>

<style lang="scss" scoped>
@import "../assets/style/vars.scss";
@import "../assets/style/mixins.scss";
@import "../assets/style/header.scss";



</style>