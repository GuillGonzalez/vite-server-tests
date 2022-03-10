<template>
  <p>Quizzes</p>
  <!-- <ul>
    <li v-for="quiz in quizzes" v-bind:key="quiz.id">
      {{ quiz.title }} <button @click="loadQuestions(quiz.id)">{{ quiz.id }}</button>
    </li>
  </ul> -->
  
  <quiz 
    v-for="quiz in quizzes"
    v-bind:key="quiz.id"
    v-bind:pkey="quiz.id"
    v-bind:title="quiz.title">
  ></quiz>

</template>

<script>
import { onMounted } from '@vue/runtime-core'
import { ref } from 'vue'
import axios from 'axios';
import { APISettings } from '../config';
import Quiz from '../components/Quiz.vue'

export default {
  name: 'Getquizzes',
  data () {
    return {
      quizzes: [],
      axiosError: ''
    }
  },
  components: {
    'quiz' : Quiz
  },
  props: {
    id: 0
  },
  setup (props) {
    const quizzes = ref([])
    const axiosError = ref('')
    const quizId = props.id
    console.log(APISettings.baseURL)
    axios.get('https://printful.com/test-quiz.php?action=quizzes')
      .then( function( response ) {
        console.log(response.data)
        quizzes.value = response.data
      }.bind(this))
      .catch( function( error ){
        axiosError = error;
      }.bind(this));
      
    return {
      quizzes,
      axiosError
    }
  }
}

</script>