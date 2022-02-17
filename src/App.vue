<template>
  <div class="container-fluid">
    <Header
    @searchForMovie="callApi"
    @searchForSeries="callApi"
    />
    
    <Main
      :popular="callPopular"
      :filmDetails="callMovies"
      :seriesDetails="callSeries"
    /> 
       


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
      apiThree : "https://api.themoviedb.org/3/movie/popular",
      urlParams: {
        api_key: 'e7257db464e5496213805673eeca26f6',
        query:'',
      },
      callMovies: [],
      callSeries: [],
      callPopular: [],
    }
  },

  mounted(){
    this.getPopular()

  },

  methods:{

    getApi(){

      let callMovie = axios.get(this.apiOne, {params: this.urlParams});
      let callSerie = axios.get(this.apiTwo, {params: this.urlParams});
      
      //console.log(callMovie);
      //console.log(callSerie);

      Promise.all([callMovie, callSerie])
      .then((r) => {
        this.callMovies = r[0].data.results;
        this.callSeries = r[1].data.results;
        
      }).catch(e => {
        console.log(e);
      })
      
    },

    getPopular(){
       axios.get(this.apiThree, {params: this.urlParams})
       .then((r) =>{
        this.callPopular = r.data.results;
         console.log('popular',this.callPopular);
       }).catch(e => {
        console.log(e);
      })


    },

    callApi(text){
      this.urlParams.query = text;
      //console.log(text);
      //console.log(this.urlParams.query);
      return this.getApi();
    },

    // callApiPopular(text){
    //   this.urlParams.query = text;
    //   //console.log(text);
    //   //console.log(this.urlParams.query);
    //   return this.getPopular();

    // },

  }

}
</script>

<style lang="scss">
@import "./assets/style/vars.scss";
@import "./assets/style/generals.scss";

</style>
