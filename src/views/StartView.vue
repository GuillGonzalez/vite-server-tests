<template>
  <div>
    <h1>Choose a quiz</h1>
    <enter-name @has_name="has_name" />
    <get-quizzes v-show="hasName"/>
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
      console.log('has name')
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