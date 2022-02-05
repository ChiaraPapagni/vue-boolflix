<template>
  <div class="card">
    <div class="poster">
      <img
        v-if="movie.backdrop_path"
        :src="'https://image.tmdb.org/t/p/w500/' + movie.backdrop_path"
        :alt="movie.title"
      />
      <img
        v-else
        src="../assets/img/not-available.png"
        alt="image not available"
      />
      <h3 class="title_on_poster">{{ movie.title }}</h3>
    </div>
    <!-- /.poster -->

    <div class="info">
      <h3 class="title"> {{ movie.title }}</h3>
      <!-- /.title -->

      <!-- <div class="language">
        <span v-if="movie.original_language == 'da'">
          <flag iso="dm" :squared="false" />
        </span>
        <span v-else-if="movie.original_language == 'en'">
          <flag iso="gb" :squared="false" />
        </span>
        <span v-else-if="movie.original_language == 'ja'">
          <flag iso="jp" :squared="false" />
        </span>
        <span v-else-if="movie.original_language == 'zh'">
          <flag iso="cn" :squared="false" />
        </span>
        <span v-else>
          <flag :iso="movie.original_language" :squared="false" />
        </span>
      </div> -->
      <!-- /.language -->

      <div class="rating">
        <span
          v-for="(vote, i) in Math.ceil(movie.vote_average / 2)"
          :key="'fas' + i"
        >
          <font-awesome-icon :icon="['fas', 'star']" />
        </span>
        <span
          v-for="(vote, i) in 5 - Math.ceil(movie.vote_average / 2)"
          :key="'far' + i"
        >
          <font-awesome-icon :icon="['far', 'star']" />
        </span>
      </div>
      <!-- /.rating -->

      <div class="overview">
        <p>
          <strong>Overview:</strong> {{ movie.overview.substr(0, 100) + "..." }}
        </p>
      </div>
      <!-- /.overview -->

      <!-- <div class="cast">
        <a @click="getCast(movie.id)">Show Cast</a>
        <span v-for="(actor, i) in cast" :key="i"> {{ actor.name }}, </span>
      </div> -->
      <!-- /.cast -->
    </div>
    <!-- /.info -->
  </div>
  <!-- /.card -->
</template>

<script>
import axios from "axios";

export default {
  props: {
    movie: Object,
  },
  data() {
    return {
      API_URL: "https://api.themoviedb.org/3/",
      API_KEY: "api_key=2424eb37f31271f5c92911aca0fd84c2",
      cast: [],
    };
  },
  mounted() {
    this.getCast();
  },
  methods: {
    getCast(id) {
      axios
        .get(`${this.API_URL}movie/${id}/credits?${this.API_KEY}`)
        .then((r) => {
          this.cast = [];
          for (let i = 0; i < 5; i++) {
            this.cast.push(r.data.cast[i]);
          }
        })
        .catch((e) => {
          console.log(e);
        });
    },
  },
};
</script>

<style lang="scss">
.card {
  .poster {
    cursor: pointer;
  }

  .info {
    width: calc(320px - 0.4rem) !important;
  }
}
</style>