<template>

  <div class="form">
    <petition-input :class="{hidden: showedInput === 'question'}" :petition="petition"></petition-input>
    <question-input :class="{hidden: showedInput === 'petition'}"></question-input>
  </div>

</template>

<script>

  import petitionInput from '@/components/petition-input'
  import questionInput from '@/components/question-input'
  import Bus from '@/utils/Bus'

  export default {
    name: 'generalForm',
    props: ['petition'],
    data () {
      return {
        showedInput: 'petition'
      }
    },
    components: {
      questionInput,
      petitionInput
    },
    created () {
      Bus.$on('petitionDone', () => {
        this.showedInput = 'question'
      })
      Bus.$on('questionDone', () => {
        this.showedInput = 'petition'
      })
    }
  }

</script>

<style>

  .form {
    background-color: #919191;
    margin: 50px 100px 0 100px;
    height: 60px;
    padding: 20px 5px 10px 5px;

  }

</style>
