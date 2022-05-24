<template>

  <main>
  
    <div v-if="movies != undefined && series != undefined" class="container">

      <div v-show="newSelect == 'movie' || newSelect == '' ">
        <h2>movies</h2>
        <div class="row _row">
          <CardComp v-for="movie in movies" :key="movie.id" :item="movie"/>
        </div>
      </div>

      <div v-show="newSelect == 'tv' || newSelect == '' ">
        <h2>series</h2>
        <div class="row _row">
          <CardComp v-for="serie in series" :key="serie.id" :item="serie"/>
        </div>
      </div>
    </div>

  </main>

</template>

<script>
import CardComp from './CardComp.vue'


export default {
  components: { CardComp },
  name: 'MainComp',

  data(){
    return {

      
    }
  },

  props: {
    movies: Array,
    series: Array,
    newSelect: String,
  },


}
</script>

<style lang="scss" scoped>
 main {
   min-height: calc(100vh - 100px);
  background-color: #434343;
  padding: 30px 0;

  & ._row {
    height: 540px;
    overflow-y: auto;
    margin-bottom: 20px;
  }

  & h2 {
    text-transform: uppercase;
    color: white;
    margin-bottom: 20px;
  }
 }
</style>