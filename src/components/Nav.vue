<template>
  <nav class="navWrapper" v-bind:class="{ dark }">
    <router-link to="/">SPACER</router-link>
    <router-link to="/about">About</router-link>
  </nav>
</template>

<script>
export default {
  name: 'Nav',
  props: {
    dark: {
      type: Boolean,
      default: false,
    },
  },
};
</script>

<style lang="scss" scoped>
  .navWrapper {
    display: flex;
    justify-content: space-between;
    align-items: center;
    height: 100%;
    margin: 0 2rem;

    a {
      font-weight: 600;
      letter-spacing: 0.2rem;
      text-decoration: none;
      text-transform: uppercase;
      position: relative;
      color: white;
    }

    a::before,
    a::after {
      transition: all 0.35s ease;
      height: 2px;
      width: 35%;
      background-color: #528cb3;
      position: absolute;
      content: '';
      opacity: 0;
    }

    a::before {
      top: -3px;
      left: 0;
    }
    a::after {
      bottom: -3px;
      right: 0;
    }
    a:hover::before,
    a:hover::after,
    a:focus::before,
    a:focus::after {
      opacity: 1;
    }
    a:hover::before,
    a:focus::before {
      left: 65%;
    }
    a:hover::after,
    a:focus::after {
      right: 65%;
    }
  }

  .dark a {
    color: #1e3d4a !important;
  }
</style>
