<template>
  <div class="discover_item">
    <div class="poster">
      <img
        v-if="item.poster_path"
        :src="'https://image.tmdb.org/t/p/w185/' + item.poster_path"
        :alt="item.title"
      />
    </div>
  </div>
  <!-- /.discover_item -->
</template>

<script>
export default {
  props: {
    item: Object,
  },
};
</script>

<style lang="scss">
.poster {
  cursor: pointer;
}
</style>