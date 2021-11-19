<template>
  <main id="site_main">
    <div class="movies">
      <h2 v-if="movies.length > 0">Movie</h2>
      <div class="movie">
        <div v-for="movie in movies" :key="movie.id">
          <Movie :movie="movie" />
        </div>
      </div>
    </div>
    <!-- /.movies -->

    <div class="tv_show">
      <h2 v-if="tvShow.length > 0">TV Show</h2>
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

  h2 {
    text-align: center;
    margin: 4rem 0 2rem 0;
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