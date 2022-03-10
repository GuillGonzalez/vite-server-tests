<template>
  <div class="results">
    <h1>This is the Questions view</h1>
    <get-quizzes/>
  </div>
</template>

<script>
import GetQuizzes from '../components/GetQuizzes.vue'

export default {
  name: 'QuestionsView',
  components: {
    GetQuizzes
  }
}
</script>
