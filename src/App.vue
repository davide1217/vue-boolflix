<template>
  <div>
    <HeaderComp :titlesSearched="titlesSearched" />
    <MainComp @titles="titles" />
  </div>
</template>

<script>
import HeaderComp from './components/HeaderComp.vue'
import MainComp from './components/MainComp.vue'


export default {
  name: 'App',
  components: {
    HeaderComp,
    MainComp
  },
  data() {
    return {
      titles: [],
    }
  },
  methods: {
    titlesSearched(datas) {
      this.titles = datas;
    }
  }
}
</script>


<style lang="scss">
  @import './assets/style/_global.scss';
 
</style>
