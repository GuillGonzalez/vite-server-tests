<template>
  <div>
    <p>Current Quiz is {{ quizId }}</p>
    <p>These are the options for question {{ questionId }}</p>
      
      <question-option
        v-for="option in questionOptions"
        v-bind:key="option.id"
        v-bind:answer="option.id"
        v-bind:title="option.title"
        @click="selectAnswer(option.id)"
      ></question-option>
<p> store: {{ store.count }} </p>
  </div>
</template>

<script>
import { onMounted } from '@vue/runtime-core'
import { ref } from 'vue'
import axios from 'axios';
import { APISettings } from '../config';
import Option from './Option.vue'
import { store } from '../store.js'

export default {
  name: 'QuestionOptions',
  data () {
    return {
      questionOptions: {},
      axiosError: '',
      store
    }
  },
  props: {
    questionId: 0,
    quizId: 0
  },
  components: {
    'question-option': Option
  },
  setup (props) {
    const questionOptions = ref([])
    const axiosError = ref('')
    axios.get(`${APISettings.baseURL}?action=answers&quizId=${props.quizId}&questionId=${props.questionId}`)
      .then( function( response ) {
        questionOptions.value = response.data
      }.bind(this))
      .catch( function( error ){
        axiosError.value = error;
      }.bind(this));
      
    return {
      questionOptions,
      axiosError
    }
  },
  methods: {
    selectAnswer(answerId) {
      store.count ++
    }
  }
}

</script>