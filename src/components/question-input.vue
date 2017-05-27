<template>

  <div>
    <label class="text" for="question">Ya que me adoras puedes preguntar:</label>
    <input class="input" id="question" v-model="question">

  </div>

</template>

<script>

  import Bus from '@/utils/Bus'

  export default {
    name: 'questionInput',
    props: [],
    data () {
      return {
        question: ''
      }
    },
    methods: {
    },
    watch: {
      question: function () {
        if (this.question.endsWith('?')) {
          this.question = ''
          Bus.$emit('questionDone')
        }
      }
    }
  }

</script>

<style>

  .input{
    width: 70%;
    border-width: 2px;
    border-color: #fa000b;
    margin-bottom: 25px;

  }

  .text{
    font-family: 'Indie Flower', cursive;
    color: whitesmoke;
  }

  .hidden-element {
    display: none;
  }

</style>
