<template>
  <question 
    v-for="(question, key ) in axiosResponse"
    v-bind:key="question.id"
    v-bind:title="question.title"
    v-bind:index="key"
    v-show="currentQuestion === key"
  ></question>

  <button @click="loadAxios()">Load Question (Axios)</button>
  <button @click="currentQuestion--">Anterior</button>
  <button @click="currentQuestion++">Siguiente</button>
  <p>{{currentQuestion}}</p>
</template>

<script>
import axios from 'axios';
import Question from './Question.vue';

export default {
    data(){
      return {
        axiosResponse: {},
        axiosError: '',
        currentQuestion: 0
      }
    },
    components: {
        'question': Question
    },
    methods: {
      loadAxios() {
        axios.get('https://printful.com/test-quiz.php?action=questions&quizId=141')
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