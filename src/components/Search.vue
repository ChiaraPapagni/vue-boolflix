<template>
  <div class="search">
    <input v-model="searchString" type="search" placeholder="Search a movie" />
    <button @click="$emit('search-items', searchString)">Search</button>
  </div>
  <!-- /.search -->
</template>

<script>
export default {
  data() {
    return {
      searchString: "",
    };
  },
};
</script>

<style lang="scss">
</style>