<template>
    <div>
      <HeaderComp @titlesSearched="titlesSearched"/>
      <MainComp :movies="movies" :series="series" />
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
      movies: [],
      series: [],
      apiUrl: 'https://api.themoviedb.org/3/search/',
      apiParams: {
        api_key: '5f4fd7f5dc5c754c3c85c2ce597184b1',
        language: 'it-IT',
        query: '',
      },
    }
  },

  methods: {

    titlesSearched(data) {
      this.apiParams.query = data;
      this.movies= [],
      this.series= [],
      this.getApi('movie', this.moviesTitles);
      this.getApi('tv', this.seriesTitles);
    },

    getApi(type) {

      if(type == 'movie') {
        axios.get(this.apiUrl + type, {
        params: this.apiParams})
        .then(res => {
          res.data.results.forEach(element => {
          this.movies.push(element)
          });
        });
      } 
      else {
        axios.get(this.apiUrl + type, {
        params: this.apiParams})
        .then(res => {
          res.data.results.forEach(element => {
          this.series.push(element)
          });
        });
      }

    }
      
    
  },

}
</script>


<style lang="scss">
  @import './assets/style/_global.scss';
 
</style>
