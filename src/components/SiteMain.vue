<template>
  <main id="site_main" class="container">
    <!-- <h2>Movie</h2> -->
    <div class="movies clearfix" v-for="movie in movies" :key="movie.id">
      <Card :item="movie"/>
    </div>
    <!-- /.movies -->

    <!-- <h2>TV Show</h2> -->
    <div class="tv_show clearfix" v-for="tv in tvShow" :key="tv.id">
      <Card :item="tv"/>
    </div>
    <!-- /.tv_show -->
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
  .container {
    width: 95%;
    margin: auto;
  }
  .movies,
  .tv_show {
    float: left;
  }
}
</style>