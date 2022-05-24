<template>
  <div v-if="item.title" class="item d-flex align-items-center m-3">
    <div class="me-5">
      <img v-if="item.poster_path == null" src="https://blog.rahulbhutani.com/wp-content/uploads/2020/05/Screenshot-2018-12-16-at-21.06.29.png" alt="">
      <img v-else :src="`https://image.tmdb.org/t/p/original/${item.poster_path}`" alt="">
    </div>
    <div class="text-center">
      <h2>Titolo: {{item.title}}</h2>
      <h4>Titolo originale: {{item.original_title}}</h4>
      <span>Lingua originale: <img :src="`https://flagcdn.com/16x12/${(item.original_language == 'en') ? 'gb' : item.original_language}.png`" alt=""> </span><br>
      <span>Voto medio: {{voteInStars()}}
        <span v-for="index in 5" :key="`starN-${index}}`">
          <span v-if="index <= stars"><i class="fa-solid fa-star"></i></span>
          <span v-else><i class="fa-regular fa-star"></i></span>
        </span>
      </span>
    </div>
  </div>

  <div v-else class="item d-flex align-items-center m-3">
    <div class="me-5">
      <img v-if="item.poster_path == null" src="https://blog.rahulbhutani.com/wp-content/uploads/2020/05/Screenshot-2018-12-16-at-21.06.29.png" alt="">
      <img v-else :src="`https://image.tmdb.org/t/p/original/${item.poster_path}`" alt="">
    </div>
    <div class="text-center">
      <h2>Titolo: {{item.name}}</h2>
      <h4>Titolo originale: {{item.original_name}}</h4>
      <span>Lingua originale: <img :src="`https://flagcdn.com/16x12/${(item.original_language == 'en') ? 'gb' : item.original_language}.png`" alt=""> </span><br>
      <span>Voto medio: {{voteInStars()}}
        <span v-for="index in 5" :key="`starN-${index}}`">
          <span v-if="index <= stars"><i class="fa-solid fa-star"></i></span>
          <span v-else><i class="fa-regular fa-star"></i></span>
        </span>
      </span>
    </div>
  </div>
</template>

<script>
export default {
  name: 'CardComp',
  data() {
    return {
      stars: '',
    }
  },
  props: {
    item : Object,
  },
  methods: {
    voteInStars() {

      const starsNotApproximated = this.item.vote_average / 2;
      console.log(starsNotApproximated);
      if(starsNotApproximated % 1 > 0.5) {
        this.stars = Math.ceil(starsNotApproximated)
      } else {
        this.stars = parseInt(starsNotApproximated)
      }

    }
  }
}
</script>

<style lang="scss" scoped>
  img {
    width: 300px;
  }

  span {
    font-size: 1.3rem;
    img {
      width: 20px;
    }
  }
</style>