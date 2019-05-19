<template>
  <div class="outerWrapper">
    <div class="innerWrapper">
      <div class="photo">
        <img v-bind:src="photo" v-bind:alt="title">
      </div>
      <div class="description">
        <h2 class="title">{{ title }}</h2>
        <p class="description">{{ description }}
        </p>
      </div>
    </div>
    <div class="close" v-on:click="$emit('closeModal')"></div>
  </div>
</template>

<script>
export default {
  name: 'Modal',
  props: {
    item: {
      type: Object,
      required: true,
    },
  },
  data() {
    return {
      photo: null,
      title: null,
      description: null,
    };
  },
  mounted() {
    this.photo = this.item.links[0].href;
    this.title = this.item.data[0].title;
    this.description = this.item.data[0].description.substr(0, 200);
  },
};
</script>

<style lang="scss" scoped>
  .outerWrapper {
    background: #f6f6f6;
    width: 100%;
    height: 100%;
    position: fixed;
    top: 0;
    left: 0;

    @media (min-width: 1024px) {
      max-width: 70%;
      height: 80%;
      left: 0;
      top: 0;
      right: 0;
      bottom: 0;
      margin: auto;
      box-shadow: 0 30px 30px -10px rgba(0,0,0, 0.2);
    }
  }

  .close {
      position: absolute;
      right: 2rem;
      top: 2rem;
      width: 40px;
      height: 40px;
      cursor: pointer;

      &::before,
      &::after {
        content: '';
        position: absolute;
        left: 10%;
        top: 50%;
        width: 30px;
        height: 2px;
        background: black;
        display: block;
      }

      &::before { transform: rotate(45deg);}
      &::after { transform: rotate(-45deg);}
    }

  .innerWrapper {
    display: flex;
    height: 100%;
    padding: 2rem;
    justify-content: center;
    align-items: center;
    flex-direction: column;

    @media (min-width: 1024px) {
      flex-direction: row;

      .photo {
        min-width: 50%;
        margin-right: 1rem;
      }
    }

    .photo {
      overflow: hidden;
      width: 100%;
      height: 100%;
      position: relative;

      img {
        display: block;
        width: 100%;
        height: auto;
        position: absolute;
        top: -9999px;
        bottom: -9999px;
        left: -9999px;
        right: -9999px;
        margin: auto;
      }
    }

    .description {
      color: #333;
    }
  }
</style>
