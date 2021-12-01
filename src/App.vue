<template>
  <div class="container-fluid">
    <Header
    @searchForMovie="getApi"/>
    <Main/>
    
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
      initURL: "https://api.themoviedb.org/3/movie/550?api_key=e7257db464e5496213805673eeca26f6&query=",
      response: {},
    }
  },

  methods:{

    getApi(title){
      axios.get(`${this.initURL}${title}`)
      .then(r =>{
          console.log('io sono r',r);
        })
    }

  }

}
</script>

<style lang="scss">
@import "./assets/style/vars.scss";
@import "./assets/style/generals.scss";

</style>
