<template>
  <div class="container-fluid">
    <Header
    @searchForMovie="callApi"/>
    <Main
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
      urlParams: {
        api_key: 'e7257db464e5496213805673eeca26f6',
        query:'',
      },
      initURLSeries : "https://api.themoviedb.org/3/search/tv",
      response: [],
    }
  },

  methods:{

    getApi(){
      
      axios.get(this.initURLMovie || this.initURLSeries, {params: this.urlParams})
      .then(r =>{
        //console.log('io sono r',r);
        this.response = r.data.results;
        console.log('response', this.response);
      }).catch(e =>{
        console.log('errore',e);
      })
  
    },

    callApi(title){
      this.urlParams.query = title;
      console.log(title);
      console.log(this.urlParams.query);

      this.getApi();
    },


  }

}
</script>

<style lang="scss">
@import "./assets/style/vars.scss";
@import "./assets/style/generals.scss";

</style>
