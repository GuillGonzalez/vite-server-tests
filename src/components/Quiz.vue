<template>
  <div>
    <h2>Quiz</h2>
    <p>Selected Quiz {{ selected_quiz }}</p>
    <get-questions
      v-bind:quizId="selected_quiz"
      ref="questions"
    ></get-questions>
  </div>
  <p>Choose another quiz <button @click="navigateToStart()">Go</button></p>
</template>

<script>
import { computed } from 'vue'
import { useStore } from 'vuex'
import store from '../store/store.js'
import GetQuestions from './GetQuestions.vue'

export default {
  setup () {
    const store = useStore()
  },
  components: {
    'get-questions': GetQuestions
  },
  data () {
    return {
      selected_quiz: computed(() => store.state.selected_quiz)
    }
  },
  methods : {
    navigateToStart () {
      this.$router.push('start')
    }
  }
}
</script>