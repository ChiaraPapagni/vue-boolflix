<template>
  <div class="movies">
    <SearchMovie :searchString="query" @search-movies="search" />

    <div class="movie" v-for="movie in movies" :key="movie.id">
      <h3>{{ movie.title }}</h3>
      <h3>{{ movie.original_title }}</h3>
      <p>{{ movie.original_languag }}</p>
      <p>{{ movie.vote_average }}</p>
    </div>
    <!-- /.movie -->
  </div>
  <!-- /.movies -->
</template>

<script>
import axios from "axios";
import SearchMovie from "./SearchMovie.vue";

export default {
  components: {
    SearchMovie,
  },
  data() {
    return {
      movies: [],
      API_URL: "https://api.themoviedb.org/3/search/movie?",
      API_KEY: "api_key=2424eb37f31271f5c92911aca0fd84c2",
      query: "",
    };
  },
  methods: {
    search(text) {
      this.query = text;
      this.callApi();
    },
    callApi() {
      axios
        .get(`${this.API_URL}${this.API_KEY}&query=${this.query}`)
        .then((r) => {
          this.movies = r.data.results;
        })
        .catch((e) => {
          console.log(e);
        });
    },
  },
};
</script>

<style lang="scss">
</style>