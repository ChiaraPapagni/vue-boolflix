<template>
  <div class="card">
    <div class="poster">
      <img
        v-if="item.backdrop_path"
        :src="'https://image.tmdb.org/t/p/w500/' + item.backdrop_path"
        :alt="item.title"
      />
      <img
        v-else
        src="../assets/img/not-available.png"
        alt="image not available"
      />
      <h3 class="title_on_poster">{{ item.name }}</h3>
    </div>
    <!-- /.poster -->

    <div class="info">
      <h3 class="title">{{ item.name }}</h3>
      <!-- /.title -->

      <!-- <div class="language">
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
      </div>-->
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
        <p>
          <strong>Overview:</strong> {{ item.overview.substr(0, 100) + "..." }}
        </p>
      </div>
      <!-- /.overview -->
    </div>
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
  .poster {
    cursor: pointer;
  }

  .info {
    width: calc(320px - 0.4rem) !important;
  }
}
</style>