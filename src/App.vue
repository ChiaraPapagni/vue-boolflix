<template>
  <div id="app">
    <SiteHeader @search-items="search" />

    <SiteMain
      :movies="movies"
      :tvShow="tvShow"
      :discoverMovie="discoverMovie"
      :discoverTv="discoverTv"
      :trendingMovie="trendingMovie"
      :trendingTv="trendingTv"
    />

    <div class="error" v-if="error !== ''">{{ error }}</div>
    <!-- /.error -->

    <SiteFooter />
  </div>
</template>

<script>
import SiteHeader from "./components/SiteHeader.vue";
import SiteMain from "./components/SiteMain.vue";
import SiteFooter from "./components/SiteFooter.vue";
import axios from "axios";

export default {
  name: "App",
  components: {
    SiteHeader,
    SiteMain,
    SiteFooter,
  },
  data() {
    return {
      movies: [],
      tvShow: [],
      API_URL: "https://api.themoviedb.org/3",
      API_KEY: "api_key=2424eb37f31271f5c92911aca0fd84c2",
      query: "",
      error: "",
      discoverMovie: [],
      discoverTv: [],
      trendingMovie: [],
      trendingTv: [],
    };
  },
  mounted() {
    axios
      .get(`${this.API_URL}/discover/movie?${this.API_KEY}`)
      .then((r) => {
        this.discoverMovie = r.data.results;
      })
      .catch((e) => {
        console.log(e);
        this.error = e;
      });
    axios
      .get(`${this.API_URL}/discover/tv?${this.API_KEY}`)
      .then((r) => {
        this.discoverTv = r.data.results;
      })
      .catch((e) => {
        console.log(e);
        this.error = e;
      });
    axios
      .get(`${this.API_URL}/trending/movie/week?${this.API_KEY}`)
      .then((r) => {
        this.trendingMovie = r.data.results;
      })
      .catch((e) => {
        console.log(e);
        this.error = e;
      });
    axios
      .get(`${this.API_URL}/trending/tv/week?${this.API_KEY}`)
      .then((r) => {
        this.trendingTv = r.data.results;
      })
      .catch((e) => {
        console.log(e);
        this.error = e;
      });
  },
  methods: {
    search(text) {
      if (text !== "") {
        this.query = text;
      }
      axios
        .get(`${this.API_URL}/search/movie?${this.API_KEY}&query=${this.query}`)
        .then((r) => {
          this.movies = r.data.results;
        })
        .catch((e) => {
          console.log(e);
          this.error = e;
        });
      axios
        .get(`${this.API_URL}/search/tv?${this.API_KEY}&query=${this.query}`)
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

.error {
  text-align: center;
}
</style>
