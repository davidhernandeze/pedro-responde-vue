<template>

  <div class="header">
    <h1>Header</h1>
  </div>

</template>

<script>

  export default {
    name: 'generalForm',
    props: ['name'],
    data () {
      return {
      }
    }
  }

</script>

<style>

  .header{
    color: whitesmoke;
    background-color: #41b883;
    height: 60px;
    width: 100%;
    border-bottom-style: solid;
    border-bottom-color: black;
    margin-bottom: 10px;
    text-align: center;
  }

  .header h1{
    margin: 0 0 0 0;
    padding-top: 10px;
    font-family: 'Indie Flower', cursive;
    border-bottom: whitesmoke;
  }

</style>
