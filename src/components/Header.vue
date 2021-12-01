<template>
  <header d-flex justify-content-between align-items-center>
    <h2>{{boolflix}}</h2>
    <div class="input-group inputFilm">
      <input type="text" class="form-control" placeholder="Cerca un film" >
      <button class="btn " type="button"> {{btn_cerca}}</button>
    </div>

  </header>
</template>

<script>
export default {
  name: "Header",

  data(){
    return {
      boolflix: "boolflix",
      btn_cerca: "cerca"
    }
  }
}
</script>

<style lang="scss" scoped>
@import "../assets/style/vars.scss";
@import "../assets/style/mixins.scss";
@import "../assets/style/header.scss";



</style>