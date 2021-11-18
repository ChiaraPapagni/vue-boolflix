<template>
  <main id="site_main">
    <SearchMovie />
    <Movies />
  </main>
  <!-- /#site_main -->
</template>

<script>
import SearchMovie from "./SearchMovie.vue";
import Movies from "./Movies.vue";

export default {
  components: {
    SearchMovie,
    Movies,
  },
};
</script>

<style lang="scss">
</style>