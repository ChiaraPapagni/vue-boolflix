<template>
  <div class="cards">
    <Search :searchString="query" @search-items="search" />

    <div class="item" v-for="(item, i) in items" :key="i">
      <img
        :src="'https://image.tmdb.org/t/p/w185/' + item.poster_path"
        :alt="item.name || item.title"
      />
      <h3>{{ item.name || item.title }}</h3>
      <h3>{{ item.original_title || item.original_name }}</h3>

      <div class="language">
        <span v-if="item.original_language == 'da'">
          <flag iso="dm" :squared="false" />
        </span>
        <span v-else-if="item.original_language == 'en'">
          <flag iso="gb" :squared="false" />
        </span>
        <span v-else-if="item.original_language == 'ja'">
          <flag iso="jp" :squared="false" />
        </span>
        <span v-else-if="item.original_language == 'zh'">
          <flag iso="cn" :squared="false" />
        </span>
        <span v-else>
          <flag :iso="item.original_language" :squared="false" />
        </span>
      </div>
      <!-- /.language -->

      <div class="rating">
        <p>{{ mathCeil(item.vote_average) }}</p>
      </div>
      <!-- /.rating -->
    </div>
    <!-- ./item -->
  </div>
  <!-- /.cards -->
</template>

<script>
import axios from "axios";
import Search from "./Search.vue";
//import LangFlag from "vue-lang-code-flags";

export default {
  components: {
    Search,
    //LangFlag,
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
    mathCeil(int) {
      return Math.ceil(int / 2);
    },
  },
};
</script>

<style lang="scss">
</style>