<template>
  <div class="m-3" action="">
  
    <input v-model.trim="apiParams.query" type="text" placeholder="cerca un titolo">
    <div id="btn" @click="getApi(), (titles.length != 0) ? $emit('titlesSearched', titles) : '' ">Cerca</div>
  
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: 'HeaderComp',

  data() {
    return {
      titles: [],
      apiUrl: 'https://api.themoviedb.org/3',
      apiMovies: '/search/movie',
      apiParams: {
        api_key: '5f4fd7f5dc5c754c3c85c2ce597184b1',
        language: 'it-IT',
        query: '',
      }
    }
  },
  methods:{

    getApi() {
      if(this.titleToSearch != '') {

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

#btn {
  display: inline-block;
  padding: 1px 10px 1.5px;
  border: 1px solid black;
  cursor: pointer;
}

</style>