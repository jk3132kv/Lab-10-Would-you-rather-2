<template>
  <div class="wyrm">

    <h2>Would you rather...</h2>

    <!-- bind value of question to h3 -->
    <h3 v-bind:value="question">{{ question }}</h3>

    <!-- radio buttons with answers bound to them with listeners for when they are changed -->
    <input type="radio" v-model="choice" v-bind:value="answer1" v-on:change="choiceMade">
    <label>{{ answer1 }}</label>

    <input type="radio" v-model="choice" v-bind:value="answer2" v-on:change="choiceMade">
    <label>{{ answer2 }}</label>

  </div>
</template>

<script>
export default {
  name: 'WouldYouRather',
  props: {
    id: Number,
    question: String,
    answer1: String,
    answer2: String,
  },
  data() {
    return {
      choice: ''
    }
  },
  methods: {

    // choices emitted to the parent, app.vue
    choiceMade() {
      this.$emit('answer-changed', this.id, this.choice)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

h3 {
  margin-bottom: 20px;
}

.wyrm {
  border: 2px black solid;
  background: linear-gradient(violet,lightskyblue);
  text-align: left;
  margin: 25px 20px 25px 20px;
  padding-left: 10px;
  padding-bottom: 10px;
}

</style>