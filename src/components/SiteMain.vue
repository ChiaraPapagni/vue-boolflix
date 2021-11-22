<template>
  <main id="site_main">
    <div class="discover">
      <h3>Discover new Movies</h3>
      <VueSlickCarousel v-bind="settings" v-if="discoverMovie.length > 0">
        <div v-for="item in discoverMovie" :key="item.id">
          <Card :item="item" />
        </div>
      </VueSlickCarousel>

      <h3>Trending Movies</h3>
      <VueSlickCarousel v-bind="settings" v-if="trendingMovie.length > 0">
        <div v-for="item in trendingMovie" :key="item.id">
          <Card :item="item" />
        </div>
      </VueSlickCarousel>

      <h3>Discover new Tv Show</h3>
      <VueSlickCarousel v-bind="settings" v-if="discoverTv.length > 0">
        <div v-for="item in discoverTv" :key="item.id">
          <Card :item="item" />
        </div>
      </VueSlickCarousel>

      <h3>Trending Tv Show</h3>
      <VueSlickCarousel v-bind="settings" v-if="trendingTv.length > 0">
        <div v-for="item in trendingTv" :key="item.id">
          <Card :item="item" />
        </div>
      </VueSlickCarousel>
    </div>
    <!-- /.discover -->

    <div class="movies">
      <h4 v-if="movies.length > 0">Movie</h4>
      <div class="movie">
        <div v-for="movie in movies" :key="movie.id">
          <Movie :movie="movie" />
        </div>
      </div>
    </div>
    <!-- /.movies -->

    <div class="tv_show">
      <h4 v-if="tvShow.length > 0">TV Show</h4>
      <div class="tv">
        <div class="tv" v-for="tv in tvShow" :key="tv.id">
          <TvShow :tv="tv" />
        </div>
      </div>
    </div>
    <!-- /.tv_show -->
  </main>
  <!-- /#site_main -->
</template>

<script>
import Card from "./Card.vue";
import Movie from "./Movie.vue";
import TvShow from "./TvShow.vue";

import VueSlickCarousel from "vue-slick-carousel";
import "vue-slick-carousel/dist/vue-slick-carousel.css";
// optional style for arrows & dots
import "vue-slick-carousel/dist/vue-slick-carousel-theme.css";

export default {
  components: {
    Card,
    Movie,
    TvShow,
    VueSlickCarousel,
  },
  props: {
    movies: Array,
    tvShow: Array,
    discoverMovie: Array,
    discoverTv: Array,
    trendingMovie: Array,
    trendingTv: Array,
  },
  data() {
    return {
      settings: {
        arrows: true,
        autoplay: false,
        centerMode: true,
        dots: false,
        responsive: [
          {
            breakpoint: 2500,
            settings: {
              slidesToShow: 8,
            },
          },
          {
            breakpoint: 1800,
            settings: {
              slidesToShow: 7,
            },
          },
          {
            breakpoint: 1700,
            settings: {
              slidesToShow: 6,
            },
          },
          {
            breakpoint: 1300,
            settings: {
              slidesToShow: 5,
            },
          },
          {
            breakpoint: 1150,
            settings: {
              slidesToShow: 4,
            },
          },
          {
            breakpoint: 972,
            settings: {
              slidesToShow: 3,
            },
          },
          {
            breakpoint: 760,
            settings: {
              slidesToShow: 2,
            },
          },
          {
            breakpoint: 480,
            settings: {
              slidesToShow: 1,
            },
          },
        ],
        rtl: true,
        slidesToShow: 6,
        speed: 1500,
      },
    };
  },
};
</script>

<style lang="scss">
#site_main {
  margin-top: 50px;

  .discover {
    width: 90%;
    margin: auto;
    h3 {
      margin: 1rem 0;
      padding-top: 2rem;
    }
    .slick-dots {
      display: none !important;
    }
  }

  h4 {
    text-align: center;
    margin-top: 4rem;
  }

  .movie,
  .tv {
    display: flex;
    justify-content: center;
    flex-wrap: wrap;
    gap: 1rem;
  }
}
</style>