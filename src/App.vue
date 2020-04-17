<template>
  <div id="app">
    <div class="nav">
      
<!--importing and showing the components-->
      <!-- <home v-if="">Home</home>
      <createsnippet v-if="">Create</createsnippet>
      <createsnippet v-if="">View Snippet</createsnippet> -->

    </div>
    
  </div>
</template>

<script>

import homepage from './pages/homepage.vue';  
import createsnippet from './components/createsnippet.vue';

export default {

  name: 'App',

  components: {

  homepage,
  createsnippet

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
  background-color: #2a3439;

}

body {
font-family: "Quicksand", sans-serif;
}

#app {
  
  letter-spacing: 0.5px;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  background-image: url('./solar-image.jpg');
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
  background-color: transparent;
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