<template>
  <header id="site_header">
    <nav class="navbar">
      <div class="left_menu">
        <img src="../assets/img/logo.png" alt="Boolflix" />
        <ul>
          <li><a href="" class="active">Home</a></li>
          <li><a href="">Serie TV</a></li>
          <li><a href="">Film</a></li>
          <li><a href="">Nuovi e popolari</a></li>
          <li><a href="">La mia lista</a></li>
        </ul>
      </div>
      <!-- /.left_menu -->

      <div class="right_menu">
        <div class="search">
          <font-awesome-icon :icon="['fas', 'search']" class="search_icon" />
          <input
            class="search_input"
            v-model="searchString"
            type="text"
            placeholder="Search"
            @keydown.enter="$emit('search-items', searchString)"
          />
          <!-- <button @click="$emit('search-items', searchString)">Search</button> -->
        </div>
        <!-- ./search -->

        <font-awesome-icon :icon="['fas', 'bell']" class="bell_icon" />
        <img src="../assets/img/user-icon.png" alt="user" class="user_image" />
        <font-awesome-icon :icon="['fas', 'sort-down']" class="arrow_icon" />
      </div>
      <!-- /.right_menu -->
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
@import "../assets/scss/variables.scss";

header {
  width: 100%;
  position: fixed;
  top: 0;
  left: 50%;
  transform: translate(-50%, 0);
  z-index: 10;
  background-color: $netflix_dark_gray;

  .navbar {
    width: 95%;
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin: 0.6rem auto;

    .left_menu {
      display: flex;
      justify-content: space-between;
      align-items: center;

      img {
        width: 100px;
        margin-right: 1rem;
      }

      ul {
        list-style: none;
        li {
          display: inline-block;
          margin-right: 1rem;
          a {
            color: #ccc;
            font-size: 0.9rem;
            text-decoration: none;
          }
          a.active {
            color: #fff;
          }
          a:hover {
            color: #aaa;
          }
        }
      }
    }

    .right_menu {
      display: flex;
      justify-content: space-between;
      align-items: center;

      .search {
        display: flex;
        align-items: center;
        flex: row nowrap;
        background-color: #111;
        border: 1px solid #fff;
        padding: 0.3rem;

        .search_input {
          width: 180px;
          background-color: #111;
          border: 1px solid transparent;
          box-shadow: none;
          outline: none;
          color: #fff;
          font-size: 1rem;
          padding-left: 0.7rem;
        }
      }

      .bell_icon {
        margin: 0 1rem;
      }

      .user_image {
        width: 32px;
        height: 32px;
        border-radius: 7px;
        margin-right: 0.5rem;
      }
    }
  }
}
</style>