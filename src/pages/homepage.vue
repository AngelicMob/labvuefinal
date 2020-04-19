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

  },


  data: () => ({

    showsnippetpage: false,

  })

};
</script>

<style scoped>
@import url("https://fonts.googleapis.com/css?family=Quicksand&display=swap%22");

body {

  font-family: 'Quicksand', sans-serif;
}

</style>