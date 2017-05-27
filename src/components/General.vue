<template>


  <div class="app">
    <app-header :name="appTitle"></app-header>
    <general-form :petition="petition"></general-form>
    <input type="hidden" v-model="answer">
    <answer-container :answer="answer" :class="{ hidden: !isAnswerVisible }"></answer-container>

  </div>

</template>

<script>

  import appHeader from '@/components/header'
  import generalForm from '@/components/General-form'
  import answerContainer from '@/components/answer-container'
  import Bus from '@/utils/Bus'

  export default {
    name: 'General',
    data () {
      return {
        petition: 'Pedro responde a mi pregunta',
        appTitle: 'Pedro Responses',
        answer: '',
        isAnswerVisible: false,
        isCheater: false
      }
    },
    created () {
      Bus.$on('petitionDone', (answer, isCheater) => {
        this.answer = answer
        this.isCheater = isCheater
      })
      Bus.$on('questionDone', this.printAnswer)
      Bus.$on('startTyping', () => { this.isAnswerVisible = false })
    },
    components: {
      appHeader,
      generalForm,
      answerContainer
    },
    methods: {
      printAnswer () {
        this.answer = (!this.isCheater) ? 'No me es posible contestar' : this.answer
        this.isAnswerVisible = true
      }
    }
  }

</script>

<style>

  body{
    margin: 0 0 0 0;
  }

  .hidden {
    display: none;
  }

</style>
