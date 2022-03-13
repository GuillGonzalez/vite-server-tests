<template>
  <div class="flex justify-center align-center flex-col">
    <h1 class="text-3xl font-bold">Technical Task</h1>
    <h2 class="text-lg">Please, enter your name and choose a quiz</h2>
    <enter-name @has_name="has_name" />
    <get-quizzes v-show="hasName"/>
    <button>Start</button>
  </div>
</template>

<script>
import GetQuizzes from '../components/GetQuizzes.vue'
import EnterName from '../components/EnterName.vue'
import { defineComponent } from "vue";

export default defineComponent ({
  name: 'Start',
  components: {
    'get-quizzes': GetQuizzes,
    'enter-name': EnterName
  },
  methods: {
    has_name() {
      this.hasName = true
    }
  },
  data() {
    let hasName = false
    return {
      hasName
    }
  }
})
</script>