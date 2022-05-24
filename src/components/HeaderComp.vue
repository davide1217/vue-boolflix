<template>
  <header>
    <h1>boolfix</h1>

    <div class="h-100 d-flex align-items-center">
      <select @change="sendSelect()" v-model="selectValue" class="me-5 ps-2">
        <option value="all">All</option>
        <option value="movie">Movies</option>
        <option value="tv">Series</option>
      </select>
      <input @keyup.enter="doEmit()" v-model.trim="query" type="text" placeholder="cerca un titolo">
    </div>
  </header>
</template>

<script>

export default {
  name: 'HeaderComp',

  data() {
    return {
      query: '',
      selectValue: 'all',
    }
  },

  methods: {
    doEmit() {
      this.$emit('titlesSearched', this.query, this.selectValue);
      this.query = '';
    },
    sendSelect() {
      this.$emit('changedSelect', this.selectValue)
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

  select {
    width: fit-content;
    height: 50%;
  }

  input {
    height: 50%;
    width: 150px;
    padding: 5px;
  }

</style>