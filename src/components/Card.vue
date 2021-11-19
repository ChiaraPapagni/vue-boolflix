<template>
  <div class="card">
    <div class="poster">
      <img
        v-if="item.poster_path"
        :src="'https://image.tmdb.org/t/p/w185/' + item.poster_path"
        :alt="item.name || item.title"
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
        <p><strong>Title:</strong> {{ item.name || item.title }}</p>
        <p>
          <strong>Original title:</strong>
          {{ item.original_title || item.original_name }}
        </p>
      </div>
      <!-- /.title -->

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
        <span
          v-for="(vote, i) in Math.ceil(item.vote_average / 2)"
          :key="'fas' + i"
        >
          <font-awesome-icon :icon="['fas', 'star']" />
        </span>
        <span
          v-for="(vote, i) in 5 - Math.ceil(item.vote_average / 2)"
          :key="'far' + i"
        >
          <font-awesome-icon :icon="['far', 'star']" />
        </span>
      </div>
      <!-- /.rating -->

      <div class="overview">
        <p><strong>Overview:</strong> {{ item.overview }}</p>
      </div>
      <!-- /.overview -->
    </div>
    <!-- /.info -->
  </div>
  <!-- /.card -->
</template>

<script>
export default {
  props: {
    item: Object,
  },
};
</script>

<style lang="scss">
.card {
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
    padding: 1rem 0.5rem;
    color: #eee;
    font-size: 0.85rem;
    opacity: 0;
    transition: opacity 0.3s;
    z-index: 1;

    div {
      padding: 0.2rem 0;
    }
    .rating {
      color: gold;
    }
    .overview {
      height: 125px;
      overflow: hidden;
      text-overflow: ellipsis;
    }
  }
}
.card:hover::after,
.card:hover .info {
  opacity: 1;
}
</style>