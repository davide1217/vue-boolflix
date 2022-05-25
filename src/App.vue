<template>
    <div>
      <HeaderComp @titlesSearched="titlesSearched" @changedSelect="changedSelect"/>
      <JumboComp :movies="jumboMovies"/>
      <MainComp :movies="movies" :series="series" :newSelect="selectValue" />
    </div>
</template>

<script>
import HeaderComp from './components/HeaderComp.vue';
import MainComp from './components/MainComp.vue';
import axios from "axios";
import JumboComp from './components/JumboComp.vue';



export default {
  name: 'App',
  components: {
    HeaderComp,
    JumboComp,
    MainComp
    
  },
  data() {
    return {
      selectValue: '',
      jumboMovies: [],
      movies: [],
      series: [],
      apiUrl: 'https://api.themoviedb.org/3/search/',
      apiUrlTrending: 'https://api.themoviedb.org/3/trending/',
      apiParams: {
        api_key: '5f4fd7f5dc5c754c3c85c2ce597184b1',
        language: 'it-IT',
        query: '',
      },
      apiParamsTrending: {
        api_key: '5f4fd7f5dc5c754c3c85c2ce597184b1',
        language: 'it-IT',
      }
    }
  },

  methods: {

    titlesSearched(title, selected) {
      this.apiParams.query = title;
      this.movies= [];
      this.series= [];
      if(selected == 'all') {
        this.getApi('movie');
        this.getApi('tv');
      } else {
        this.selectValue = selected;
        this.getApi(selected);
      }
    },

    changedSelect(value) {
      this.selectValue = '';
      this.movies = [];
      this.series = [];
      if (this.apiParams.query == '' && value != 'all') {
        this.selectValue = value;
        this.getTrandingApi(`${value}/day`)
      } 
      else if (this.apiParams.query == '' && value == 'all') {
        this.getTrandingApi('movie/day');
        this.getTrandingApi('tv/day');
      }
      else if (this.apiParams.query != '' && value != 'all') {
        this.selectValue = value;
        this.getApi(value)
      } else {
        this.getApi('movie');
        this.getApi('tv');
      }
    },

    getApi(type) {

      axios.get(this.apiUrl + type, {
      params: this.apiParams})
      .then(res => {
        res.data.results.forEach(element => {
          if (type == 'movie') {
            this.movies.push(element)
          } else {
            this.series.push(element)
          }
        });
      });

    },

    getTrandingApi(type) {
      axios.get(this.apiUrlTrending + type, {
      params: this.apiParamsTrending})
      .then(res => {
        res.data.results.forEach(element => {
        if (type == 'movie/day') {
          this.jumboMovies.push(element);
          this.movies.push(element)
        } else {
          this.series.push(element)
        }
        });
      });
    }
  },

  mounted() {
    this.getTrandingApi('movie/day');
    this.getTrandingApi('tv/day');
  }
}
</script>


<style lang="scss">
  @import './assets/style/_global.scss';
 
</style>
