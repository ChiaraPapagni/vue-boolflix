<template>
  <div id="app">
    <SiteHeader @search-items="search" />
    <SiteMain :movies="movies" :tvShow="tvShow" />
    <div class="error" v-if="error !== ''">{{ error }}</div>
    <!-- /.error -->
  </div>
</template>

<script>
import SiteHeader from "./components/SiteHeader.vue";
import SiteMain from "./components/SiteMain.vue";
import axios from "axios";

export default {
  name: "App",
  components: {
    SiteHeader,
    SiteMain,
  },
  data() {
    return {
      movies: [],
      tvShow: [],
      API_URL: "https://api.themoviedb.org/3/search/",
      API_KEY: "api_key=2424eb37f31271f5c92911aca0fd84c2",
      query: "",
      error: "",
    };
  },
  methods: {
    search(text) {
      if (text !== "") {
        this.query = text;
      }
      axios
        .get(`${this.API_URL}movie?${this.API_KEY}&query=${this.query}`)
        .then((r) => {
          this.movies = r.data.results;
          console.log(
            `${this.API_URL}movie?${this.API_KEY}&query=${this.query}`
          );
        })
        .catch((e) => {
          console.log(e);
          this.error = e;
        });
      axios
        .get(`${this.API_URL}tv?${this.API_KEY}&query=${this.query}`)
        .then((r) => {
          this.tvShow = r.data.results;
        })
        .catch((e) => {
          console.log(e);
          this.error = e;
        });
    },
  },
};
</script>

<style lang="scss">
@import "./assets/scss/variables.scss";
@import "./assets/scss/common.scss";
</style>
