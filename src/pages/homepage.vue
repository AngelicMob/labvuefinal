<template>
  <div class="home">
   
      <div class="content">
        <createsnippet />
        <snippet />
      </div>

    
  </div>
</template>


<script>
import snippet from 'src/components/snippet.vue';
export default {
  name: 'homepage',
  components: {
    
    snippet,
    createsnippet

  }
,

data: () => ({


}),

methods: {


}

} 


</script>

<style scoped>

</style>