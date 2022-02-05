<template>
  <footer id="site_footer">
    <p class="copyright">
      Copyright ©
      <a href="https://github.com/ChiaraPapagni" target="_blank"
        >ChiaraPapagni</a
      >. All Rights Reserved
    </p>
    <p>
      Thank
      <a href="https://www.themoviedb.org/" target="_blank"
        >The Movie Database</a
      >
      for API
      <font-awesome-icon :icon="['far', 'heart']" />
    </p>
  </footer>
  <!-- /#site_footer -->
</template>

<script>
export default {};
</script>

<style lang="scss">
@import "../assets/scss/variables.scss";

footer {
  margin: 3rem 0;
  color: #d3d3d3;
  font-weight: bold;
  text-align: center;
  letter-spacing: 0.03rem;

  p.copyright {
    font-size: 1rem;
    padding-bottom: 0.5rem;
    a {
      background: linear-gradient(to right, #fca764 0%, #dd6682 100%);
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
    }
  }

  p {
    font-size: 0.95rem;
    a {
      background: linear-gradient(to right, #c0fecf 0%, #1ed5a9 100%);
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      font-size: 1rem;
      text-decoration: none;
    }
  }
}
</style>