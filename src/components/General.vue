<template>


  <div class="app">
    <app-header :name="appTitle"></app-header>
  </div>

</template>

<script>

  import appHeader from '@/components/header'

  export default {
    name: 'General',
    data () {
      return {
        appTitle: 'Pedro Responses'
      }
    },
    components: {
      appHeader
    }
  }

</script>

<style>

  body{
    margin: 0 0 0 0;
  }
  div{
    background-color: #6fe1ff;
  }

</style>
