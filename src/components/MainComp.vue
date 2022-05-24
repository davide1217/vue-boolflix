<template>

  <main>
  
    <div v-if="movies != undefined && series != undefined" class="container">
      <div class="row">
        <CardComp v-for="movie in movies" :key="movie.id" :item="movie"/>
        <CardComp v-for="serie in series" :key="serie.id" :item="serie"/>
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
  },


}
</script>

<style lang="scss" scoped>
 main {
   min-height: calc(100vh - 100px);
  background-color: #434343;
  padding: 30px 0;
 }
</style>