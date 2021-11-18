<template>
  <main id="site_main">
    <Cards :items="items" />
  </main>
  <!-- /#site_main -->
</template>

<script>
import Cards from "./Cards.vue";

export default {
  components: {
    Cards,
  },
  props: {
    items: Array,
  },
};
</script>

<style lang="scss">
</style>