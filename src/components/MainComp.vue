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
export default {
  name: 'MainComp',

  data(){
    return {
      
    }
  },

  props: {
    titles: Array,
  },

}
</script>

<style lang="scss" scoped>


</style>