<template>
  <div class="film">
    <h5>{{title}}</h5>
    <h6>{{titleOriginal}}</h6>
    <h6>{{lang}}</h6>
    <h6>{{vote}}</h6>
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
}
</script>

<style lang="scss" scoped>
@import "../assets/style/vars.scss";
@import "../assets/style/mixins.scss";
@import "../assets/style/film.scss";


</style>