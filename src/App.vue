<template>
  <div id="app">
    <nav id="nav">
      <router-link to="/">SPACER</router-link>
      <router-link to="/about">About</router-link>
    </nav>
    <router-view/>
  </div>
</template>

<style lang="scss">
  @import url('https://fonts.googleapis.com/css?family=Montserrat:300,400,600,800');

  * {
    box-sizing: border-box;
    margin: 0;
    color: white;
  }

  body {
    font-family: 'Montserrat', sans-serif;
    background-image: url("./assets/heroimage.jpg");
    background-repeat: no-repeat;
    background-position: 10%;
    background-size: cover;
    height: 100vh;
  }

  #nav {
    display: flex;
    justify-content: space-between;
    width: 90%;
    margin: 1rem auto;

    a {
      text-decoration: none;
      text-transform: uppercase;
    }
  }
</style>
