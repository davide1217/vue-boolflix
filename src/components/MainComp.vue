<template>

  <div class="container">

    <div v-for="film in titles" :key="film.id" class="item d-flex m-3">
      <div class="me-2"><img :src="`https://image.tmdb.org/t/p/original/${film.poster_path}`" alt=""></div>
      <div class="text-center">
        <h2>{{film.title}}</h2>
        <h4>{{film.original_title}}</h4>
        <span>{{film.original_language}}</span><br>
        <span>{{film.vote_average}}</span>
      </div>
    </div>

  </div>

</template>

<script>
import axios from "axios";

export default {
  name: 'MainComp',

  data(){
    return {
      titles: [],
      apiUrl: 'https://api.themoviedb.org/3',
      apiMovies: '/search/movie',
      apiParams: {
        api_key: '5f4fd7f5dc5c754c3c85c2ce597184b1',
        language: 'it-IT',
        query: this.titles,
      }
    }
  },

  props: {
    titlesToSearch: String,
  },

  mounted() {
    this.getApi();
  },

  methods:{

    getApi() {
      if(this.titleToSearch != undefined) {

        this.titles = [];
        axios.get(this.apiUrl+this.apiMovies, {
        params: this.apiParams
        }).then( res => {
        this.titles = res.data.results
        })
      }
    }
  }

}
</script>

<style lang="scss" scoped>


</style>