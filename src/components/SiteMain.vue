<template>
  <main id="site_main">
    <div class="movies clearfix">
      <h2 v-if="movies.length > 0">Movie</h2>
      <div class="movie" v-for="movie in movies" :key="movie.id">
        <Movie :movie="movie" />
      </div>
    </div>
    <!-- /.movies -->

    <div class="tv_show clearfix">
      <h2 v-if="tvShow.length > 0">TV Show</h2>
      <div class="tv" v-for="tv in tvShow" :key="tv.id">
        <TvShow :tv="tv" />
      </div>
    </div>
    <!-- /.tv_show -->
  </main>
  <!-- /#site_main -->
</template>

<script>
import Movie from "./Movie.vue";
import TvShow from "./TvShow.vue";

export default {
  components: {
    Movie,
    TvShow,
  },
  props: {
    movies: Array,
    tvShow: Array,
  },
};
</script>

<style lang="scss">
#site_main {
  width: 95%;
  margin: 4rem auto;

  .movie,
  .tv {
    float: left;
  }

  .clearfix::after {
    content: "";
    display: table;
    clear: both;
  }
}
</style>