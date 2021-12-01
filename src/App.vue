<template>
  <div class="container-fluid">
    <Header
    @searchForMovie="getApi"/>
    <Main/>
    
  </div>
</template>

<script>
import Header from "./components/Header.vue"
import Main from "./components/Main.vue"

export default {
  name: 'App',
  components: {
    Header,
    Main,
  },

  data(){
    return {
      initURL: "https://api.themoviedb.org/3/movie/550",
    }
  },

  methods:{
    getApi(){

    }
  }

}
</script>

<style lang="scss">
@import "./assets/style/vars.scss";
@import "./assets/style/generals.scss";

</style>
