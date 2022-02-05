<template>
  <div class="hero_image">
    <img
      :src="'https://image.tmdb.org/t/p/original/' + item.backdrop_path"
      :alt="item.title"
    />
    <div class="info_film">
      <h1 class="title">{{ item.title }}</h1>
      <p class="desc">
        {{ item.overview }}
      </p>
      <div class="actions">
        <div class="rating">
          <PercentageCircle
            :percent="getPercent(item.vote_average)"
            :active-color="
              getPercent(item.vote_average) > 50 ? 'green' : 'orange'
            "
            complete-color="green"
            :animate="true"
            size="medium"
          />
        </div>
        <!-- /.rating -->
        <a class="icon_circle_play" href="#">
          <font-awesome-icon class="play" :icon="['fas', 'play']" />
        </a>
        <a class="icon_circle_add" href="#">
          <font-awesome-icon class="add" :icon="['fas', 'plus']" />
        </a>
        <a class="icon_circle_star" href="#">
          <font-awesome-icon class="star" :icon="['fas', 'star']" />
        </a>
      </div>
    </div>
  </div>
  <!-- /.hero_image -->
</template>

<script>
import PercentageCircle from "vue-css-percentage-circle";

export default {
  components: {
    PercentageCircle,
  },
  props: {
    item: Object,
  },
  methods: {
    getPercent(rating) {
      return Math.floor((rating * 100) / 10);
    },
  },
};
</script>

<style lang="scss">
.hero_image {
  width: 100%;
  position: relative;
  height: 500px;
  margin-top: 3rem;

  .info_film {
    position: absolute;
    max-width: 42%;
    top: 8rem;
    left: 2rem;
    padding: 4%;
    color: #efefef;
    letter-spacing: 0.02rem;

    .title {
      font-size: 35px;
      color: #fefefe;
    }

    .desc {
      display: -webkit-box;
      -webkit-line-clamp: 4;
      -webkit-box-orient: vertical;
      overflow: hidden;
      margin: 1rem 0;
      font-size: 18px;
      line-height: 1.6rem;
    }

    .actions {
      display: flex;
      align-items: center;
      margin-top: 1rem;

      a {
        display: flex;
        align-items: center;
        justify-content: center;
        color: #efefef;
        margin-right: 1rem;

        &.icon_circle_play {
          width: 50px;
          height: 50px;
          background-color: #ddd;
          border-radius: 50%;
          margin-left: 1rem;
          padding: 0.7rem;
          padding-left: 0.9rem;
          color: #675f5d;

          &:hover {
            background-color: #fff;
            transform: 0.3s;
          }
        }

        &.icon_circle_add,
        &.icon_circle_star {
          width: 50px;
          height: 50px;
          border: 2px solid #ffffff80;
          border-radius: 50%;
          padding: 0.7rem;

          &:hover {
            color: #fff;
            border: 3px solid #fff;
            transform: 0.3s;
          }
        }

        &.icon_circle_add {
        }

        &.icon_circle_star {
          padding-top: 0.5rem;
        }

        & > .play,
        & > .add,
        & > .star {
          font-size: 1.4rem;
        }
      }
    }
  }

  & > img {
    width: 100%;
    height: 700px;
    object-fit: cover;
    object-position: center;
    opacity: 0.4;
  }
}
</style>