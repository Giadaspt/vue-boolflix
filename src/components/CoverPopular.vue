<template>
  <section class="container-fluid d-flex">

    <div class="d-flex row">
      <div class="flip-card " 
       @click="on()">
        <div class="flip-card-inner">

          <!-- image card front -->
          <div class="flip-card-front">
            <img class="cover" :src="getPoster()" @error="replace" alt="">
          </div>
          <div 
          class="flip-card-back">
          
            <h5>{{objItems.title}} </h5>
            <h5>{{objItems.name}} </h5>
            <h6 
              v-if="titleSec !== titleOriginalSec">
              {{objItems.titleOriginal}}
            </h6>

            <!-- flags -->
            <img 
            class="flag"
            v-if="image == getFlag() && gotNoFlag() !== image"
            :src="getFlag()" :alt="objItems.title">
            <h6 v-if="gotNoFlag() == image"> 
              Lingua: {{objItems.original_language}}
            </h6>

          <!-- stars -->
            <div>
              <i
                v-for="(i, index) in 5" :key="`full${index}`"
                :class="i < stars(objItems.vote_average) ? 'fas fa-star' : 'far fa-star' ">
              </i>
            </div>

            <!-- description -->
            <p class="overview ">{{textCut(objItems.overview)}}...</p>
          </div>
        </div>
      </div>
    </div>


    <!-- Modal -->
    <section class="contain " >
      <div class="col modalMovie" v-if="toggleModal">
        <div class="box">
          <div class="leftModal">
            <h5>{{objItems.title}} </h5>
              <h5>{{objItems.name}} </h5>
              <h6 
                v-if="titleSec !== titleOriginalSec">
                {{objItems.titleOriginal}}
              </h6>

              <!-- flags -->
              <img 
              class="flag"
              v-if="image == getFlag() && gotNoFlag() !== image"
              :src="getFlag()" :alt="objItems.title">
              
              <h6 v-if="gotNoFlag() == image"> 
                Lingua: {{objItems.original_language}}
              </h6>

              <!-- stars -->
              <div class="stars">
                <i
                  v-for="(i, index) in 5" :key="`full${index}`"
                  :class="i < stars(objItems.vote_average) ? 'fas fa-star' : 'far fa-star' ">
                </i>
              </div>

              <!-- description -->
              <p class="overModal">
                {{objItems.overview}}
              </p>
          </div>
          <div class="rightModal">
               <img class="cover" :src="getPoster()" @error="replace" alt="">
          </div>

          <!-- closing cross -->
          <button class="closingModal" v-if="!toggleModel"
          @click="off()">
            X
          </button>
        </div>
      </div>
    </section>
  </section>

</template>

<script>

export default {
  name: "CoverPopular",

  props:['objItems'],

  data(){
    return {
      image: this.objItems.original_language,
      base: 'https://image.tmdb.org/t/p/w342',
      cutText: this.objItems.overview,
      titleSec: this.objItems.title,
      titleOriginalSec: this.objItems.titleOriginal,
      toggleModal: false,
    }
  },


  methods:{

    getFlag(){
      if (this.objItems.original_language == 'en'){
        this.image = require('../assets/img/en.png');
      } else if (this.objItems.original_language == 'it'){
        this.image = require('../assets/img/it.png');
      } 
      return this.image
    },

    gotNoFlag(){
      if (this.image !== 'en' || this.image !== 'it'){
        return this.objItems.original_language
      }
    },

    getPoster() {
      return this.base+this.objItems.poster_path;
    },

    replace(e) {
      //console.log("404");
      e.target.src = require("../assets/img/nonecares.jpg")
    },

    stars() {
     let voted = this.objItems.vote_average;
      const count = Math.ceil(voted / 2);
      return count
    },

    textCut(){
      return this.cutText.slice(0,80)
    },

    on(){
        this.toggleModal = true;
      },

    off(){
      this.toggleModal = false;
    }

  },
}
</script>

<style lang="scss" scoped>
@import "../assets/style/vars.scss";
@import "../assets/style/mixins.scss";
@import "../assets/style/film_series.scss";



</style>