<template>
  <div>
    <ul>
      <li>{{ title }} <button @click="loadQuestions(pkey)">{{ pkey }}</button></li>
    </ul> 
    <!-- <get-questions v-bind:quizId="pkey" ref="questions"/> -->
  </div>
</template>

<script>
import { useStore } from 'vuex'
import store from '../store/store.js'

export default {
  name: 'Quiz',
  setup () {
    const store = useStore()
  },
  props: {
    title: '',
    pkey: 0
  },
  methods: {
    loadQuestions(quizId) {
      //this.$refs.questions.fetchQuestions(quizId);
      store.commit('set_current_quiz', quizId);
      this.$router.push('questions')
    }
  }
}
</script>