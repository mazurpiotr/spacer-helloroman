<template>
  <section class="searchWrapper">
    <input type="search"
           name="search"
           id="search"
           placeholder="e.g. Titan"
           v-model='searchValue'
           v-on:input="handleInput">
  </section>
</template>

<script>
export default {
  name: 'SearchInput',
  data() {
    return {
      searchValue: '',
      results: [],
    };
  },
};
</script>

<style lang="scss" scoped>
  .searchWrapper {
    display: flex;
    flex-direction: column;
    align-items: center;
    width: 250px;

    input {
    height: 50px;
    border: none;
    border-bottom: 1px solid white;
    background: none;
    }
  }
</style>
