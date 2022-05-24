<template>

  <main>
  
    <div v-if="movies != undefined || series != undefined" class="m-1">

    <CardComp v-for="movie in movies" :key="movie.id" :item="movie"/>
    <CardComp v-for="serie in series" :key="serie.id" :item="serie"/>

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

</style>