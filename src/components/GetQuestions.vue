<template>
<p>Current Quiz is {{ quizId }}</p>

  <question 
    v-for="(question, key ) in axiosResponse"
    v-bind:key="question.id"
    v-bind:questionId="question.id"
    v-bind:title="question.title"
    v-bind:quizId="quizId"
    v-show="currentQuestion === key"
  ></question>

  <button @click="currentQuestion--">Back</button>
  <button @click="currentQuestion++">Next</button>
  <p>This Quizz has {{ axiosResponse.length }} questions</p>
  <p>Current question: {{ currentQuestion + 1}}</p>
</template>

<script>
import axios from 'axios';
import Question from './Question.vue';
import { APISettings } from '../config';

export default {
    data() {
      return {
        axiosResponse: {},
        axiosError: '',
        currentQuestion: 0
      }
    },
    props: {
      quizId: 0
    },
    components: {
        'question': Question,
    },
    methods: {
      loadAxios(quizzId) {
        axios.get(APISettings.baseURL + '?action=questions&quizId=' + quizzId)
          .then( function( response ){
            this.axiosResponse = response.data;
          }.bind(this))
          .catch( function( error ){
            this.axiosError = error;
        }.bind(this));
      }
  }
}
</script>