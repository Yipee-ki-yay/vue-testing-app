<template>
  <div id="app">
    <app-header></app-header>
    <app-form></app-form>  
  </div>
</template>

<script>
  import AppHeader from './components/Header.vue';
  import AppForm from './components/Form.vue';
    
  export default {    
    components: {
    AppHeader,
    AppForm
    }
  }
</script>

<style>

</style>
