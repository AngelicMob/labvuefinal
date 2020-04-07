<template>
  <div class="home">
   
      <div class="content">
        <Snippet />
      </div>
    
  </div>
</template>


<script>
import snippet from 'src/components/snippet.vue';
export default {
  name: 'homepage',
  components: {
    Snippet
  }
}
</script>

<style scoped>

body {

    background-image: url(././galaxy-purple)
}
</style>