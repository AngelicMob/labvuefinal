<template>
  <div class="home">
   
      <div class="content">
        <snippet />
        <createsnippet />
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
,

data: () => ({


}),

methods: {


}

} 


</script>

<style scoped>

</style>