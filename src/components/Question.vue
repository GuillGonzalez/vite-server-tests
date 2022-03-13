<template>
  <div>
    <div>
      <p> {{ title }}</p>
      <question-options
        v-bind:quizId="quizId"
        v-bind:questionId="questionId"
      ></question-options>
    </div>
  </div>
</template>

<script>
  import QuestionOptions from './QuestionOptions.vue'

  export default {
    name: 'Question',
    props: {
      title: '',
      questionId: 0,
      quizId: 0
    },
    components: {
      'question-options': QuestionOptions
    }
  }

</script>