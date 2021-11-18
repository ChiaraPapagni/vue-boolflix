<template>
  <div class="cards">
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
    </div>
    <!-- ./item -->
  </div>
  <!-- /.cards -->
</template>

<script>
export default {
  props: {
    items: Array,
  },
};
</script>

<style lang="scss">
</style>