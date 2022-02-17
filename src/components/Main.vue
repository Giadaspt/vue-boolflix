<template>
  <main class="container-fluid">

    <!-- popular movies -->
    <section class="mb-4"
    v-show="filmDetails.length === 0 && seriesDetails.length === 0">
      <h3 class="title" > Most Popular </h3> 
      <section class="popular" >
        
        <VueSlickCarousel
          v-bind="settings"
          ref="carouselTv">

          <CoverPopular
            v-for="(movie, index) in popular " 
            :key="`movie${index}`"
            :objItems = "movie"
            />

        </VueSlickCarousel>
      </section>
    </section>

    <!-- movies -->
    <h3 class="title" v-show="filmDetails.length > 0">Film</h3>

      <VueSlickCarousel
        v-bind="settings"
        ref="carouselTv">
      <CoverMovie
        v-for="(film, index) in filmDetails " 
        :key="`film${index}`"
        :objItems = "film" />
      </VueSlickCarousel>
   

    <!-- series -->
    <h3 class="title" v-show="seriesDetails.length > 0">Series</h3> 

    <VueSlickCarousel
        v-bind="settings"
        ref="carouselTv">

      <CoverMovie
        v-for="(serie, index) in seriesDetails " 
        :key="`serie${index}`"
        :objItems = "serie"
        />

    </VueSlickCarousel>

  </main>
</template>

<script>
import CoverMovie from "./CoverMovie.vue";
import CoverPopular from "./CoverPopular.vue";
import VueSlickCarousel from 'vue-slick-carousel';
import 'vue-slick-carousel/dist/vue-slick-carousel.css';
import 'vue-slick-carousel/dist/vue-slick-carousel-theme.css';

export default {
  name: "Main",

  components:{
    CoverMovie,
    CoverPopular,
    VueSlickCarousel,
  },

  props:{
    filmDetails: Array,
    seriesDetails: Array,
    popular: Array,
  },

  data(){
    return {
      show: false,
      index: -1,

     settings: {
        "dots": true,
        "focusOnSelect": false,
        "infinite": false,
        "speed": 500,
        "slidesToShow": 4,
        "slidesToScroll": 4,
        "touchThreshold": 10,
        "variableWidth": true,
        "variableHeight": true
      }
    }
  },

  method:{
    showNext(type) {
         if (
           type === 'filmDetails' ||
           type === 'seriesDetails' ||
           type === 'popular'
           ) this.$refs.carouselMovie.next();
         else this.$refs.carouselTv.next();
      },
      showPrev(type) {
         if (
           type === 'filmDetails' ||
           type === 'seriesDetails' ||
           type === 'popular'
         ) this.$refs.carouselMovie.prev();
         else this.$refs.carouselTv.prev();
      },
  }
}
</script>

<style lang="scss" scoped>
@import "../assets/style/vars.scss";
@import "../assets/style/mixins.scss";
@import "../assets/style/main.scss";

</style>