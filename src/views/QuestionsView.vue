<template>
  <div class="results">
    <h1>This is the Questions view</h1>
    <quiz></quiz>
  </div>
</template>

<script>
import Quiz from '../components/Quiz.vue'

export default {
  name: 'QuestionsView',
  components: {
    Quiz
  }
}
</script>
