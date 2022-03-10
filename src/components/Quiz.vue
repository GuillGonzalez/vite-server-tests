<template>
  <h3>This is the quiz {{ pkey }}</h3>
  {{ title }} <button @click="loadQuestions(pkey)">{{ pkey }}</button>

  <get-questions v-bind:quizId="pkey" ref="questions"/>
  
</template>

<script>
import GetQuestions from '../components/GetQuestions.vue'
export default {
  name: 'Quiz',
  props: {
    title: '',
    pkey: 0
  },
  methods: {
    loadQuestions(quizId) {
      this.$refs.questions.loadAxios(quizId)
    }
  },
  components: {
    'get-questions': GetQuestions
  }
}

</script>
