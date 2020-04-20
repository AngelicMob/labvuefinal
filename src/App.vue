<template>
  <div id="app">
    <div class="nav">
        <homepage />


    </div>

  </div>
</template>

<script>

import homepage from './pages/homepage.vue';

export default {

name: 'App',

  components: {

    homepage,

  },


  data: () => ({


  }),


  methods: {



  }

  };


</script>

<style>

@import url("https://fonts.googleapis.com/css?family=Quicksand&display=swap%22");


*{
  padding: 0;
  margin: 0;
  /* background-color: #2a3439; */

}

body {
font-family: "Quicksand", sans-serif;
}

#app {

  letter-spacing: 0.5px;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  background-image: url('assets/solar-image.jpg');
  background-position: center;
  background-repeat: no-repeat;
  background-color: #141e22;
  background-attachment: fixed;
  background-size: cover;
  -webkit-background-size: cover;
  -moz-background-size: cover;
  -o-background-size: cover;
  height: 100vh;
  z-index: -1;
  overflow: auto;

}


.nav {
  display: flex;
  justify-content: space-around;
  align-items: center;
  min-height: 100px;

  }


  .nav a {
      color: white;
      letter-spacing: 2px;
      font-weight: normal;
      font-size: 14px;
      text-decoration-line: none;
  }
  .nav li {
      list-style: none;
  }

</style>