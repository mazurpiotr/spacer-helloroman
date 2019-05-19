<template>
  <section class="about">
    <header>
      <Nav/>
    </header>
    <HeroImage/>
    <div class="lorem">
      <h1>This is an about page</h1>
      <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Voluptates similique labore voluptas atque accusamus quam laudantium voluptatem in? Eligendi suscipit ratione neque at dolorem reprehenderit illum, architecto dignissimos impedit itaque maxime, dolores facilis!</p>
    </div>
  </section>
</template>

<script>
import Nav from '@/components/Nav.vue';
import HeroImage from '@/components/HeroImage.vue';

export default {
  components: {
    Nav,
    HeroImage,
  },
};
</script>

<style lang="scss" scoped>
  header {
    height: 10vh;
    width: 100%;
  }

  .lorem {
    min-height: 90vh;
    display: flex;
    text-align: center;
    justify-content: center;
    flex-direction: column;
    align-items: center;
    color: white;

    h1 {
      letter-spacing: 5px;
    }

    p {
      width: 60%;
      margin: 1rem;
      letter-spacing: 1px;
    }
  }
</style>
