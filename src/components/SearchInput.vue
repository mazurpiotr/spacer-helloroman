<template>
  <section class="searchWrapper">
    <input type="search"
           name="search"
           placeholder="e.g. Titan"
           v-bind:class="{ dark }"
           v-bind:value="value"
           v-on:input="handleChange">
  </section>
</template>

<script>
export default {
  name: 'SearchInput',
  props: {
    value: {
      type: String,
      required: true,
    },
    dark: {
      type: Boolean,
      default: false,
    },
  },
  methods: {
    handleChange(e) {
      this.$emit('input', e.target.value);
    },
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
    text-align: center;
    font-size: 1.2rem;
    font-weight: 300;
    height: 50px;
    border: none;
    border-bottom: 1px solid white;
    background: none;
    transition: box-shadow 0.3s;
    color: white;
    }

    input:hover,
    input:focus {
      outline: none;
      box-shadow: 0 15px 15px -13px rgba(255, 255, 255, 0.6);
    }
  }

  .dark {
    color: #1e3d4a !important;
    border-bottom-color: #1e3d4a !important;
  }

  .dark:hover,
  .dark:focus {
    outline: none;
    box-shadow: 0 15px 15px -13px rgba(#1e3d4a, 0.6) !important;
  }
</style>
