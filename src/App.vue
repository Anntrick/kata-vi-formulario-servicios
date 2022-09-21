<template>
  <form-services></form-services>
</template>

<script lang="ts">
  import { defineComponent } from 'vue';
  import FormServices from './components/FormServices.vue'
  
  
  export default defineComponent({
    name: 'App',
    components: {
      FormServices
    }
  });
</script>

<style scoped>

</style>
