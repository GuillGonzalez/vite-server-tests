<script setup>
import { RouterLink, RouterView } from 'vue-router'
import HelloWorld from '@/components/HelloWorld.vue'
</script>

<template>
  <header>
    <div class="wrapper">
      <nav>
        <RouterLink to="/start">Start</RouterLink>
        <RouterLink to="/questions">Questions</RouterLink>
        <RouterLink to="/results">Results</RouterLink>
      </nav>
    </div>
  </header>

  <RouterView />
</template>

<style>

</style>
