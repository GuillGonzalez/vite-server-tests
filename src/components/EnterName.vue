<template>
  <form>
    <label for="playerName">Enter name</label><br/>
    <input 
      v-model="player_name"
      type="text"
      name="playerName"
      placeholder="Anonyme"
      @focus="$emit('has_name')"
      @focusout="enter_name"/>
  </form>
</template>

<script>
import { computed } from 'vue'
import { useStore } from 'vuex'
import store from '../store/store.js'
import { defineComponent } from "vue";

export default defineComponent ({
  'name': 'EnterName',
  setup() {
    const store = useStore()
  },
  emits: ['has_name'],
  data() {
    return {
      player_name: computed(() => store.state.player_name)
    }
  },
  methods: {
    enter_name(_e) {
      store.commit('set_player_name', _e.target.value)
      this.$parent.$emit('has_name');
    }
  }
})

</script>
