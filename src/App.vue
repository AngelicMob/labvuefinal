<template>
  <div id="app">
    <div class="nav">
      
      <li><a href="">Home</a></li>
      <li><a href="">Create</a></li>
      <li><a href="">View snippets</a></li>
       
    </div>
    
  </div>
</template>

<script>


export default {

  name: 'App'
  }

</script>

<style>


*{
  padding: 0;
  margin: 0;
  background-color: #2a3439;
}

#app {
  
  font-family: 'Orbitron', sans-serif, monospace;
  letter-spacing: 2px;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  
  color: #2c3e50;
  background-image: url('./solar-image.jpg');
  height: 100vh;
  background-position: center;
  background-repeat: no-repeat;
  background-size: cover; 
  background-color: #141e22;
  background-size: cover;
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




/*testing2 that is original with the vue thing
#nav {
  padding: 20px;
  float: left;
  color: antiquewhite;
}
#nav a {
  font-weight: normal;
  color: antiquewhite;
  margin: 1em;
  text-decoration-line: none;
  display: block;
}
*/

</style>