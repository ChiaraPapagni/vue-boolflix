<template>
  <div class="cards">
    <Search :searchString="query" @search-items="search" />

    <div class="item" v-for="(item, i) in items" :key="i">
      <h3>{{ item.name || item.title }}</h3>
      <h3>{{ item.original_title || item.original_name }}</h3>
      <LangFlag :iso="item.original_language" :squared="false" />
      <p>{{ item.vote_average }}</p>
      <!-- ./item -->
    </div>
  </div>
  <!-- /.cards -->
</template>

<script>
import axios from "axios";
import Search from "./Search.vue";
import LangFlag from "vue-lang-code-flags";

export default {
  components: {
    Search,
    LangFlag,
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
    callApi() {
      axios
        .get(`${this.API_URL}movie?${this.API_KEY}&query=${this.query}`)
        .then((r) => {
          this.items = r.data.results;
        })
        .catch((e) => {
          console.log(e);
        });
      axios
        .get(`${this.API_URL}tv?${this.API_KEY}&query=${this.query}`)
        .then((r) => {
          this.items = r.data.results;
        })
        .catch((e) => {
          console.log(e);
        });
    },
    search(text) {
      this.query = text;
      this.callApi();
    },
  },
};
</script>

<style lang="scss">
</style>