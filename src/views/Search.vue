<template>
  <main class="wrapper">
    <Claim/>
    <SearchInput/>
  </main>
</template>

<script>
import Claim from '@/components/Claim.vue';
import SearchInput from '@/components/SearchInput.vue';

import axios from 'axios';
import debounce from 'lodash.debounce';

const API = 'https://images-api.nasa.gov/search';

function getImages() {
  axios.get(`${API}?q=${this.searchValue}&media_type=image`)
    .then((res) => {
      this.results = res.data.collection.items;
    })
    .catch((err) => {
      console.log(err);
    });
}

export default {
  name: 'search',
  data() {
    return {
      searchValue: '',
      results: [],
    };
  },
  components: {
    Claim,
    SearchInput,
  },
  methods: {
    handleInput: debounce(getImages, 500),
  },
};
</script>

<style lang="scss" scoped>
  .wrapper {
    display: flex;
    flex-direction: column;
    align-items: center;
    margin: 0;
    padding: 2em;
    width: 100%;
  }
</style>
