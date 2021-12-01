<template>
  <div class="container-fluid">
    <Header
    @searchForMovie="getApi"/>
    <Main
    :filmDetails="response.results"/>
    
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
      initURL : "https://api.themoviedb.org/3/search/movie?api_key=e7257db464e5496213805673eeca26f6&query=",
      response: {},
    }
  },

  methods:{

    getApi(title){

      // movie -> https://api.themoviedb.org/3/search/movie?api_key=CHIAVE_TUA&query=TITOLO'
      // serie tv -> https://api.themoviedb.org/3/search/tv?api_key=CHIAVE_TUA&query=TITOLO'
      
      const queryChiamata = `${this.initURL}${title}`;

      console.log('query', queryChiamata);

      axios.get(queryChiamata)
      .then(r =>{
        //console.log('io sono r',r);
        this.response = r.data.results;
        console.log('response', this.response);
      }).catch(e =>{
        console.log('errore',e);
      })

      // axios.get(`${this.initURL}${title}`)
      // .then(r =>{
      //   //console.log('io sono r',r);
      //   this.response = r.data;
      //   console.log('response', this.response);
      // }).catch(e =>{
      //   console.log('errore',e);
      // })      
    }

  }

}
</script>

<style lang="scss">
@import "./assets/style/vars.scss";
@import "./assets/style/generals.scss";

</style>
