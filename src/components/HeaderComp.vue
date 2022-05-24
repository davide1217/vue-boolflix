<template>
  <header>
    <h1>boolfix</h1>
    <input @keyup.enter="doEmit()" v-model.trim="query" type="text" placeholder="cerca un titolo">
  </header>
</template>

<script>

export default {
  name: 'HeaderComp',

  data() {
    return {
      
      query: '',
      
    }
  },

  methods: {
    doEmit() {
      this.$emit('titlesSearched', this.query);
      this.query = '';
    }
  }
}
</script>

<style lang="scss" scoped>

  header {
    height: 100px;
    background-color: black;
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 20px;
  }

  h1 {
    text-transform: uppercase;
    color: red;
  }

  input {
    height: 50%;
    width: 13%;
    padding: 5px;
  }

</style>