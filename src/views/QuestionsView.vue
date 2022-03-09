<template>
  <div class="results">
    <h1>This is the Questions view</h1>
    <get-quizes/>
    <get-questions/>
  </div>
</template>

<script>
import GetQuizes from '../components/GetQuizes.vue'
import GetQuestions from '../components/GetQuestions.vue'

export default {
  name: 'QuestionsView',
  components: {
    GetQuizes,
    GetQuestions
  }
}
</script>
