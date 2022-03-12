<template>
  <div>
    <p>Current Quiz is {{ quizId }}</p>

    <item-question 
      v-for="(item, key) in questions"
      v-bind:key="item.id"
      v-bind:questionId="item.id"
      v-bind:title="item.title"
      v-bind:quizId="quizId"
      v-show="currentQuestion === key"
    ></item-question>

    <button @click="decrement()">Back</button>
    <button @click="increment()">Next</button>

    <p>This Quizz has {{ questions.length }} questions</p>
    <p>Current question: {{ currentQuestion + 1}}</p>
    <button 
      v-show="currentQuestion == questions.length -1"
      @click="navigateToResults()">Show Results</button>
  </div>
</template>

<script>
import axios from 'axios';
import Question from './Question.vue';
import { APISettings } from '../config';
import { ref } from 'vue'

export default {
  setup (props) {
    const questions = ref([])
    const axiosError = ref('')
    axios.get(APISettings.baseURL + '?action=questions&quizId=' + props.quizId)
      .then( function( response ){
        questions.value = response.data;
      }.bind(this))
      .catch( function( error ){
        axiosError.value = error;
    }.bind(this));
    return {
      axiosError,
      questions
    }
  },
  data() {
    return {
      axiosError: '',
      currentQuestion: 0,
    }
  },
  props: {
    quizId: 0
  },
  components: {
      'item-question': Question,
  },
  methods: {
    increment() {
      ++this.currentQuestion > (this.questions.length-1)
      ? this.currentQuestion = (this.questions.length-1)
      : this.currentQuestion
    },
    decrement() {
      --this.currentQuestion < 0
      ? this.currentQuestion = 0
      : this.currentQuestion
    },
    navigateToResults() {
      this.$router.push('results')
    }
  }
}
</script>