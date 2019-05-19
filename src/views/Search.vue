<template>
  <div>
    <header>
        <Nav v-bind:dark="step === 1"/>
    </header>
    <div v-bind:class="[{ flexStart: step === 1}, 'wrapper']">
      <transition name="slide">
        <img src="../assets/logo.svg" alt="SPACER" class="logo" v-if="step === 1">
      </transition>
      <transition name="fade">
        <HeroImage v-if="step === 0"/>
      </transition>
      <Claim v-if="step === 0"/>
      <SearchInput
        v-model='searchValue'
        v-on:input="handleInput"
        v-bind:dark="step === 1"/>
      <div class="results" v-if="results && !loading && step === 1">
        <Item
          v-for="item in results"
          v-bind:item="item"
          v-bind:key="item.data[0].nasa_id"
          v-on:click.native="handleModalOpen(item)"/>
      </div>
      <Loader v-if="loading" v-bind:dark="step === 1"/>
    </div>
    <Modal
      v-if="modalOpen"
      v-bind:item="modalItem"
      v-on:closeModal="modalOpen = false"/>
  </div>
</template>

<script>
import Nav from '@/components/Nav.vue';
import HeroImage from '@/components/HeroImage.vue';
import Claim from '@/components/Claim.vue';
import SearchInput from '@/components/SearchInput.vue';
import Item from '@/components/Item.vue';
import Modal from '@/components/Modal.vue';
import Loader from '@/components/Loader.vue';

import axios from 'axios';
import debounce from 'lodash.debounce';

const API = 'https://images-api.nasa.gov/search';

export default {
  name: 'search',
  data() {
    return {
      modalOpen: false,
      modalItem: null,
      loading: false,
      step: 0,
      searchValue: '',
      results: [],
    };
  },
  components: {
    Nav,
    HeroImage,
    Claim,
    SearchInput,
    Item,
    Modal,
    Loader,
  },
  methods: {
    handleModalOpen(item) {
      this.modalOpen = true;
      this.modalItem = item;
    },
    // eslint-disable-next-line
    handleInput: debounce(function () {
      this.loading = true;
      axios.get(`${API}?q=${this.searchValue}&media_type=image`)
        .then((res) => {
          this.results = res.data.collection.items;
          this.loading = false;
          this.step = 1;
        })
        .catch((err) => {
          console.log(err);
        });
    }, 500),
  },
};
</script>

<style lang="scss" scoped>
  .wrapper {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    margin: 0;
    padding: 2em;
    min-height: 90vh;

    &.flexStart {
      justify-content: flex-start;
    }
  }

  .fade-enter-active, .fade-leave-active {
    transition: opacity .5s;
  }

  .fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
    opacity: 0;
  }

  .slide-enter-active, .slide-leave-active {
    transition: margin-top .5s ease;
  }

  .slide-enter, .slide-leave-to /* .fade-leave-active below version 2.1.8 */ {
    margin-top: -100px;
  }

  header {
    height: 10vh;
    width: 100%;
  }

  .logo {
    margin-bottom: 1rem;
  }

  .results {
    margin-top: 2rem;
    display: grid;
    grid-template-columns: 1fr 1fr;
    grid-gap: 1.4rem;

    @media (min-width: 768px) {
      grid-template-columns: 1fr 1fr 1fr;
    }
  }
</style>
