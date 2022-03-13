<template>
  <div>
    <ul>
      <li class="transition ease-in-out hover:shadow-md">
        <button @click="loadQuestions(pkey)">
          <span
            class="check-icon"
            v-show="pkey == current_quiz">✔️</span>
          {{ title }}
        </button>
      </li>
    </ul> 
  </div>
</template>

<script>
import { useStore } from 'vuex'
import store from '../store/store.js'
import { ref } from 'vue'
import { computed } from 'vue'

export default {
  name: 'Quiz',
  setup () {
    const store = useStore()
    const selected = ref(false)
    return {
      current_quiz: computed(() => store.state.selected_quiz),
      selected
    }
  },
  props: {
    title: '',
    pkey: 0,
  },
  methods: {
    loadQuestions(quizId) {
      store.commit('set_current_quiz', quizId);
      this.selected = true;
      this.$parent.$emit('select');
      //this.$router.push('questions')
    }
  }
}
</script>

<style scoped>

button {
  position: relative
}
.check-icon {
  position: absolute;
  left: -24px;
}

</style>