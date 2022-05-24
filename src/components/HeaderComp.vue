<template>
  <div class="m-3" action="">
  
    <input v-model.trim="query" type="text" placeholder="cerca un titolo">
    <div id="btn" @click="doEmit()">Cerca</div>
  
  </div>
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

#btn {
  display: inline-block;
  padding: 1px 10px 1.5px;
  border: 1px solid black;
  cursor: pointer;
}

</style>