<template>
  <pre>{{ axiosResponse }}</pre>
  <button @click="loadAxios()">Load Companies (Axios)</button>
</template>

<script>
import axios from 'axios';

export default {
    data(){
        return {
            axiosResponse: {},
            axiosError: ''
        }
    },

    methods: {
        loadAxios(){
            axios.get('https://printful.com/test-quiz.php?action=quizzes')
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