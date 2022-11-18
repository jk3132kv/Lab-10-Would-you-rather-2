<template>
  <div class="app">

      <h1>Would You Rather?</h1>

      <!-- gets the template from WouldYouRather.vue -->
      <!-- v-for to loop over questions array -->
      <!-- v-bind for questions and answers and id values to child -->
      <would-you-rather 
      v-for="question in questions" 
      v-bind:id = "question.id"
      v-bind:question="question.question"
      v-bind:answer1="question.answer1"
      v-bind:answer2="question.answer2"
      v-on:answer-changed="answerChanged">
      </would-you-rather>

      <h1>You Would Rather...</h1>

      <!-- loops to display each choice -->
      <p v-for="choice in choices">{{ choice }}</p>

  </div>
</template>

<script>

// connects the WouldYouRather component
import WouldYouRather from './components/WouldYouRather.vue'

export default {
  name: 'App',
  components: {
    WouldYouRather
  },

  // questions array data
  data() {
    return {
      questions: [
        {
          id: 0,
          question: 'be super fast or super strong?',
          answer1: 'Be super fast',
          answer2: 'Be super strong'
        },
        {
          id: 1,
          question: 'be invisible or have the ability to fly?',
          answer1: 'Be invisible',
          answer2: 'Have the ability to fly'
        },
        {
          id: 2,
          question: 'have an elephant-sized cat or a cat-sized elephant?',
          answer1: 'Have an elephant-sized cat',
          answer2: 'Have a cat-sized elephant'
        },
      ],
      choices: []
    }
  },
  methods: {

    // funcion to display answer1 or answer2 depending on which radio button is pushed
    // not sure if this will work having trouble getting answers to display
    answerChanged(id, choice) {
      this.choices[id] = choice
    }
  }
}
</script>

<style>

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #734896;
  margin-top: 20px;
  padding-top: 20px;
  padding-bottom: 30px;
  background: lightseagreen;
}

</style>