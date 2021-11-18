<template>
  <header id="site_header">
    <nav class="navbar">
      <ul>
        <li><a href="" class="active">Home</a></li>
        <li><a href="">Serie TV</a></li>
        <li><a href="">Film</a></li>
        <li><a href="">Originali</a></li>
        <li><a href="">Aggiunti di recente</a></li>
        <li><a href="">La mia lista</a></li>
      </ul>

      <div class="search">
        <input
          v-model="searchString"
          type="search"
          placeholder="Search a movie"
          @keydown.enter="$emit('search-items', searchString)"
        />
        <button @click="$emit('search-items', searchString)">Search</button>
      </div>
      <!-- ./search -->
    </nav>
    <!-- /.navbar -->
  </header>
  <!-- /#site_header -->
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
.navbar {
  ul {
    list-style: none;
    li {
      display: inline-block;
      margin: 1rem;
      a {
        color: #bbb;
        text-decoration: none;
      }
      a.active {
        color: #fff;
      }
      a:hover {
        color: #fff;
      }
    }
  }
}
</style>