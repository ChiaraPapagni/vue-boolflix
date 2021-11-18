<template>
  <div id="app">
    <SiteHeader @search-items="search" />
    <SiteMain :items="items" />
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
      items: [],
      API_URL: "https://api.themoviedb.org/3/search/",
      API_KEY: "api_key=2424eb37f31271f5c92911aca0fd84c2",
      query: "",
    };
  },
  methods: {
    search(text) {
      const query = text;
      axios
        .get(`${this.API_URL}movie?${this.API_KEY}&query=${query}`)
        .then((r) => {
          this.items = r.data.results;
          console.log(query);
          console.log(`${this.API_URL}movie?${this.API_KEY}&query=${query}`);
        })
        .catch((e) => {
          console.log(e);
        });
      axios
        .get(`${this.API_URL}tv?${this.API_KEY}&query=${query}`)
        .then((r) => {
          this.items = r.data.results;
        })
        .catch((e) => {
          console.log(e);
        });
    },
  },
};
</script>

<style lang="scss">
@import "./assets/scss/variables.scss";
@import "./assets/scss/common.scss";
</style>
