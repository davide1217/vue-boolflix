<template>

  <main>
    <div v-if="titlesToSearch != undefined" class="m-1">

    <div  v-for="film in titlesToSearch" :key="film.id" class="item d-flex align-items-center m-3">
      <div class="me-5">
      <img v-if="film.poster_path == null" src="https://blog.rahulbhutani.com/wp-content/uploads/2020/05/Screenshot-2018-12-16-at-21.06.29.png" alt="">
      <img v-else :src="`https://image.tmdb.org/t/p/original/${film.poster_path}`" alt="">
      </div>
      <div class="text-center">
        <h2>Titolo: {{film.title}}</h2>
        <h4>Titolo originale: {{film.original_title}}</h4>
        <span>Lingua originale: <span class="text-uppercase">{{film.original_language}}</span></span><br>
        <span>Voto medio: {{film.vote_average}}</span>
      </div>
    </div>

  </div>
  </main>

</template>

<script>

export default {
  name: 'MainComp',

  data(){
    return {

      
    }
  },

  props: {
    titlesToSearch: Array,
  },

  methods:{

  }

}
</script>

<style lang="scss" scoped>
  img {
    width: 300px;
  }

  span {
    font-size: 1.3rem;
  }

</style>