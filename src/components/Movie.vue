<template>
  <div class="movie">
    <div class="poster">
      <img
        v-if="movie.poster_path"
        :src="'https://image.tmdb.org/t/p/w185/' + movie.poster_path"
        :alt="movie.name || movie.title"
      />
      <img
        v-else
        src="../assets/img/not-available.png"
        alt="image not available"
      />
    </div>
    <!-- /.poster -->

    <div class="info">
      <div class="title">
        <p><strong>Title:</strong> {{ movie.name || movie.title }}</p>
        <p>
          <strong>Original title:</strong>
          {{ movie.original_title || movie.original_name }}
        </p>
      </div>
      <!-- /.title -->

      <div class="language">
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
      </div>
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

      <div class="cast">
        <a @click="getCast(movie.id)">Show Cast</a>
        <span v-for="(actor, i) in cast" :key="i"> {{ actor.name }}, </span>
      </div>
      <!-- /.cast -->
    </div>
    <!-- /.info -->
  </div>
  <!-- /.movie -->
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
.movie {
  cursor: pointer;
  position: relative;

  img {
    width: 185px;
    height: 280px;
    padding: 0.2rem;
    object-fit: cover;
  }

  .info {
    width: calc(100% - 0.4rem);
    height: calc(100% - 0.6rem);
    position: absolute;
    top: 0.2rem;
    left: 0.2rem;
    background-color: rgba($color: #000000, $alpha: 0.7);
    padding: 0.7rem 0.5rem;
    color: #eee;
    font-size: 0.85rem;
    opacity: 0;
    transition: opacity 0.3s;
    z-index: 1;
    overflow-y: hidden;
    padding-bottom: 0.2rem;

    div {
      padding: 0.2rem 0;
    }

    .rating {
      color: gold;
    }

    .cast {
      a {
        text-decoration: underline;
      }
    }
  }
}
.movie:hover::after,
.movie:hover .info {
  opacity: 1;
}
</style>