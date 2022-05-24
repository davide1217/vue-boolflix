<template>
  <span>Voto medio: {{voteInStars()}}
    <span v-for="index in 5" :key="`starN-${index}}`">
      <span v-if="index <= stars"><i class="fa-solid fa-star"></i></span>
      <span v-else><i class="fa-regular fa-star"></i></span>
    </span>
  </span>
</template>

<script>
export default {
  name: 'RatingComp',

  data() {
    return {
      stars: '',
    }
  },
  
  props: {
    rating: Number,
  },

  methods: {
    voteInStars() {

      const starsNotApproximated = this.rating / 2;

      if(starsNotApproximated % 1 > 0.5) {
        this.stars = Math.ceil(starsNotApproximated)
      } else {
        this.stars = parseInt(starsNotApproximated)
      }

    }
  }
}
</script>

<style lang="scss" scoped>

</style>