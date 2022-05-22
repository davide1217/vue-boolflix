<template>
    <div>
      <HeaderComp @titlesSearched="titlesSearched" />
      <MainComp :titlesToSearch="titles" />
    </div>
</template>

<script>
import HeaderComp from './components/HeaderComp.vue';
import MainComp from './components/MainComp.vue';
import axios from "axios";


export default {
  name: 'App',
  components: {
    HeaderComp,
    MainComp
  },
  data() {
    return {
      titles: [],
      apiUrl: 'https://api.themoviedb.org/3',
      apiMovies: '/search/movie',
      apiParams: {
        api_key: '5f4fd7f5dc5c754c3c85c2ce597184b1',
        language: 'it-IT',
        query: '',
      },
    }
  },

  methods: {
    titlesSearched(data) {
      this.titles = [];
      this.apiParams.query = data;
      
      axios.get(this.apiUrl+this.apiMovies, {
      params: this.apiParams
      }).then( res => {
      this.titles = res.data.results;
      })
    }
  }
}
</script>


<style lang="scss">
  @import './assets/style/_global.scss';
 
</style>
