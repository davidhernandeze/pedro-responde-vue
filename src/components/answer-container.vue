<template>

  <div class="response-container">
    <div class="response-header"> Pedro responde: </div>
    {{answer}}
  </div>

</template>

<script>

  // import Bus from '@/utils/Bus'

  export default {
    name: 'answerContainer',
    props: ['answer'],
    data () {
      return {
      }
    },
    methods: {
    }
  }

</script>

<style>

  .response-container{
    color: #851a18;
    text-align: center;
    margin-top: 20px;
    font-family: 'Rock Salt', cursive;
    font-size: 50px;
  }

  .response-header{
    color: #851a18;
    text-align: left;
    margin-top: 20px;
    font-family: 'Rock Salt', cursive;
    font-size: 20px;
  }
</style>
