<template>
  <div class="heroImage"></div>
</template>

<script>
export default {
  name: 'HeroImage',
};
</script>

<style lang="scss" scoped>
  .heroImage {
    position: fixed;
    z-index: -100;
    top: 0;
    width: 100%;
    height: 100vh;
    background-image: url("../assets/heroimage.jpg");
    background-repeat: no-repeat;
    background-position: 10%;
    background-size: cover;
  }

  .heroImage::after {
    position: absolute;
    content: '';
    top: 0;
    left: 0;
    width: 100%;
    height: 100vh;
    background-color: rgba(0, 0, 0, 0.3);
  }
</style>
