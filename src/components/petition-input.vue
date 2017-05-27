<template>

  <div class="petitionInput">
    <label class="text" for="petition">Realiza la oración:</label>
    <i :title="petitionHelper" class="material-icons" style="font-size:15px; margin-top: 7px">help</i>
    <input class="input" id="petition" v-model="input" @input="transformInput($event)">
    <br>
  </div>

</template>

<script>

  import Bus from '@/utils/Bus'

  var isCheater = false
  var mantraIndex = 0

  export default {
    name: 'petitionInput',
    props: ['petition'],
    data () {
      return {
        input: '',
        answer: '',
        petitionHelper: this.petition + ':'
      }
    },
    methods: {
      transformInput () {
        if (this.input.length === 1) {
          Bus.$emit('startTyping')
        }
        if (this.input.startsWith('.')) {
          isCheater = true
          this.input = this.petition.charAt(mantraIndex)
          mantraIndex++

          return
        }
        if (this.input.endsWith(':')) {
          if (!isCheater) {
            if (this.input !== this.mantra + ':') {
              // Disparar evento para mostrar el mensaje
              this.input = ''
              return
            }
          }
          this.input = this.petition + ':'

          this.input = ''
          mantraIndex = 0
          Bus.$emit('petitionDone', this.answer, isCheater)

          return
        }
        if (mantraIndex > 0) {
          this.storeSecretInput()
          this.input = this.input.slice(0, -1)
          this.input = this.input.concat(this.petition.charAt(mantraIndex))

          mantraIndex++
        }
      },
      storeSecretInput () {
        this.answer = this.answer.concat(this.input.slice(-1))
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
