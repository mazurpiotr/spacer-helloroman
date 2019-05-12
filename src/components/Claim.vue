<template>
  <section class="claimWrapper">
    <h1 class="claim">SPACER</h1>
    <!-- eslint-disable-next-line -->
    <p class="subclaim">Begin your journey through our amazing galaxy, and discover places you never even heard of.</p>
    <p class="subclaim">Type anything space-related to start.</p>
  </section>
</template>

<script>
export default {
  name: 'Claim',
};
</script>

<style lang="scss" scoped>
  .claimWrapper {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    text-align: center;

    .claim {
      font-size: 4em;
    }

    .subclaim {
      font-size: 0.8em;
      margin: 1rem 0;
    }
  }
</style>
