<template>
  <main id="site_main" class="container">
    <div class="row">
      <h2>Movie</h2>
      <div class="movies clearfix" v-for="movie in movies" :key="movie.id">
        <Card :item="movie" class="movie" />
      </div>
      <!-- /.movies -->
    </div>

    <div class="row">
      <h2>TV Show</h2>
      <div class="tv_show clearfix" v-for="tv in tvShow" :key="tv.id">
        <Card :item="tv" />
      </div>
      <!-- /.tv_show -->
    </div>
  </main>
  <!-- /#site_main -->
</template>

<script>
import Card from "./Card.vue";

export default {
  components: {
    Card,
  },
  props: {
    movies: Array,
    tvShow: Array,
  },
};
</script>

<style lang="scss">
#site_main {
  margin-top: 4rem;

  .row {
    width: 100%;
  }
  .movies,
  .tv_show {
    float: left;
  }
}
</style>