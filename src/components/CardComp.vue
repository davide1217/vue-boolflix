<template>
  <div v-if="item.title" class="col-6 col-lg-4 _col">
    <div class="h-100 position-relative">

      <img v-if="item.poster_path == null" src="https://blog.rahulbhutani.com/wp-content/uploads/2020/05/Screenshot-2018-12-16-at-21.06.29.png" alt="">
      <img v-else :src="`https://image.tmdb.org/t/p/w342/${item.poster_path}`" alt="">

      <div>
        <div class="mb-3"><strong class="text-uppercase">Titolo:</strong> {{item.title}}</div>
        <div v-show="item.title != item.original_title" class="mb-3"><strong class="text-uppercase">Titolo originale:</strong> {{item.original_title}}</div>
        <p v-show="item.overview != '' ">Descrizione: {{item.overview}}</p>
        <span>Lingua originale: <img :src="`https://flagcdn.com/16x12/${(item.original_language == 'en') ? 'gb' : item.original_language}.png`" alt=""> </span><br>
        <RatingComp :rating="item.vote_average" />
      </div>
    </div>
  </div>

  <div v-else class="col-6 col-lg-4 _col">
    <div class="h-100 position-relative">

      <img v-if="item.poster_path == null" src="https://blog.rahulbhutani.com/wp-content/uploads/2020/05/Screenshot-2018-12-16-at-21.06.29.png" alt="">
      <img v-else :src="`https://image.tmdb.org/t/p/w342/${item.poster_path}`" alt="">
      
      <div>
        <div class="mb-3"><strong class="text-uppercase">Titolo:</strong> {{item.name}}</div>
        <div v-show="item.name != item.original_name" class="mb-3"><strong class="text-uppercase">Titolo originale:</strong> {{item.original_name}}</div>
        <p v-show="item.overview != '' ">Descrizione: {{item.overview}}</p>
        <span>Lingua originale: <img :src="`https://flagcdn.com/16x12/${(item.original_language == 'en') ? 'gb' : item.original_language}.png`" alt=""> </span><br>
        <RatingComp :rating="item.vote_average" />
      </div>
    </div>
  </div>
</template>

<script>
import RatingComp from './RatingComp';

export default {
  components: { RatingComp },
  name: 'CardComp',
  data() {
    return {

    }
  },
  props: {
    item : Object,
  },
  methods: {
    
  }
}
</script>

<style lang="scss" scoped>

  ._col {
    display: flex;
    justify-content: center;
    align-items: center;
    margin-bottom: 50px;
    height: 516px;

    & > div {
      width: 346px;
      border: 2px solid white;
      overflow: hidden;
      
      & > img {
        position: absolute;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);
        transition: .5s all;
      }

      & > div {
        position: absolute;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);
        width: 100%;
        height: 100%;
        display: flex;
        flex-direction: column;
        padding: 20px;
        transition: .5s all;
        opacity: 0;

        & p {
          max-height: 150px;
          overflow-y: auto;
        } 
      }

      &:hover > img {
        opacity: 0;
      }

      &:hover > div {
        opacity: 1;
        background-color: rgb(14, 14, 14);
        color: #727272;
      }
    }

  }

  span {
    font-size: 1.3rem;
    img {
      width: 20px;
    }
  }
</style>