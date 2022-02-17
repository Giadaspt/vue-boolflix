<template>
  <section class="head mt-4" >
    <div class="d-flex justify-content-between align-items-center">
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
    </div>

    <section class="jumbotron">

        <img src="https://staticr1.blastingcdn.com/media/photogallery/2021/11/16/os/b_1200x675/spider-man-no-way-home-si-avvicina-luscita_2689974.jpg" alt="">
        <div class="trama">
            <h5>
              L'identità dell'Uomo Ragno viene rivelata a tutti, e non riesce più a separare la sua vita normale dalla vita da supereroe, e quando chiede aiuto al Dottor Strange, lo costringe a scoprire cosa significa veramente essere l'Uomo Ragno.
            </h5>
            <button> <i class="fas fa-play"></i> Riproduci </button>
            <button class="btn-list"> <i class="fas fa-check"></i> Aggiungi alla lista </button>
        </div>
    </section>
  </section>
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