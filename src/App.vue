<template>
  <div class="container-fluid">
    <Header
    @searchForMovie="callApi"
    @searchForSeries="callApiSeries"/>
    <Main
    :seriesDetails="response"
    :filmDetails="response"/>
    
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
      initURLMovie : "https://api.themoviedb.org/3/search/movie",
      initURLSeries : "https://api.themoviedb.org/3/search/tv",
      urlParams: {
        api_key: 'e7257db464e5496213805673eeca26f6',
        query:'',
      },
      response: [],
    }
  },

  methods:{

    getApiMovie(){
      
      axios.get(this.initURLMovie, {params: this.urlParams})
      .then(r =>{
        //console.log('io sono r',r);
        this.response = r.data.results;
        console.log('response', this.response);
      }).catch(e =>{
        console.log('errore',e);
      })
  
    },

    getApiSeries(){
      
      axios.get(this.initURLSeries, {params: this.urlParams})
      .then(r =>{
        //console.log('io sono r',r);
        this.response = r.data.results;
        console.log('response series', this.response);
      }).catch(e =>{
        console.log('errore',e);
      })
  
    },

    callApi(text){
      this.urlParams.query = text;
      console.log(text);
      console.log(this.urlParams.query);

      this.getApiMovie();
      console.log('movie api', this.getApiMovie());
    },

    callApiSeries(text){
      this.urlParams.query = text;
      console.log(text);
      console.log(this.urlParams.query);
     
      this.getApiSeries();
      console.log('series api', this.getApiSeries());

    },


  }

}
</script>

<style lang="scss">
@import "./assets/style/vars.scss";
@import "./assets/style/generals.scss";

</style>
