<template>
  <main class="wrapper">
    <section class="search">
      <label for="search">Search</label>
      <input type="search"
             name="search"
             id="search"
             placeholder="e.g. Titan"
             v-model='searchValue'
             v-on:input="handleInput">
    </section>
    <section class="gallery">
        <img v-for="item in results"
            v-bind:key="item.data[0].nasa_id"
            v-bind:src="item.links[0].href"
            alt="">
    </section>
  </main>
</template>

<script>
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
    padding: 20px;
    width: 100%;
  }

  .search {
    display: flex;
    flex-direction: column;
    align-items: center;
    width: 200px;
  }

  label {
    font-family: Montserrot, sans-serif;
  }

  input {
    height: 50px;
    border: none;
    border-bottom: 1px solid #333;
  }

  .gallery {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    flex-grow: 0;

    img {
      margin: 10px;
      width: 25%;
      object-fit: contain;
    }
  }
</style>
