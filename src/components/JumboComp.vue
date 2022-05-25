<template>
  <div :style="background" class="jumbotron">
    <h1>{{movies[counter].title}}</h1>
  </div>
</template>

<script>
export default {
  name: 'JumboComp',
  props: {
    movies: Array,
  },
  data() {
    return {
      counter: 0,
    }
  },
  methods: {
    changeImg() {
      setInterval(() => {
        if(this.counter < this.movies.length - 1) {
          this.counter++
        } else {
          this.counter = 0;
        }
      }, 2500);
    },
  },
  mounted() {
    this.changeImg();
  },
  computed: {
    background() {
      return {"--backgroundImage": `url(https://image.tmdb.org/t/p/w342${this.movies[this.counter].backdrop_path})`}
    }
  }
}
</script>

<style lang="scss" scoped>
.jumbotron {
  height: 70vh;
  overflow-y: hidden;
  background-image: var(--backgroundImage);
  background-size: cover;

  h1 {
    color: rgb(175, 175, 175);
    margin: 30px;
  }
}
</style>