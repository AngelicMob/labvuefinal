<template>
  <div class="home">

      <div class="content">
        <createsnippet />
        <snippet />
      </div>
  </div>
</template>


<script>
import snippet from '@/components/snippet.vue';
import createsnippet from '@/components/createsnippet.vue';


  export default {

    name: 'homepage',
      components: {
      snippet,
      createsnippet

  }

};
</script>

<style scoped>

@import url("https://fonts.googleapis.com/css?family=Quicksand&display=swap%22");

  * {

    font-family: 'Quicksand', sans-serif;

  }


/* .button {
  background-color: #00877C;
  border: none;
  border-radius: 2px;
  color: white;
  padding: 16px 32px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 16px;
  margin: 4px 2px;
  transition-duration: 0.4s;
  cursor: pointer;
  font-weight: bold;
  margin-left: 34px;

}

.btn-view {

  background-color: #00877C;
  color: white;



}

.btn-view:hover {

  background-color: white;
  color: black;
  border: 2px solid #00877C;

} */


</style>