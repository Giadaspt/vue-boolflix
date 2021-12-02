<template>
  <div class="container-fluid">
    <Header
    @searchForMovie="callApi"
    @searchForSeries="callApi"/>
    <Main
    :seriesDetails="callSeries"
    :filmDetails="callMovies"/>
    
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import Main from "./components/Main.vue";
import axios from "axios";

export default {
  name: 'App',
  components: {
    Header,
    Main,
  },

  data(){
    return {
      apiOne : "https://api.themoviedb.org/3/search/movie",
      apiTwo : "https://api.themoviedb.org/3/search/tv",
      urlParams: {
        api_key: 'e7257db464e5496213805673eeca26f6',
        query:'',
      },
      callMovies: [],
      callSeries: [],
    }
  },

  methods:{

    getApi(){

      let callMovie = axios.get(this.apiOne, {params: this.urlParams});
      let callSerie = axios.get(this.apiTwo, {params: this.urlParams});
      console.log(callMovie);
      console.log(callSerie);

      Promise.all([callMovie, callSerie])
      .then((r) => {
        this.callMovies = r[0].data.results;
        this.callSeries = r[1].data.results;
      }).catch(e => {
        console.log(e);
      })
      
    },

    callApi(text){
      this.urlParams.query = text;
      //console.log(text);
      //console.log(this.urlParams.query);

      this.getApi();
    },

  }

}
</script>

<style lang="scss">
@import "./assets/style/vars.scss";
@import "./assets/style/generals.scss";

</style>
