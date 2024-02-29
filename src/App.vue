<script setup>
import { RouterView } from 'vue-router'
</script>

<template>
  <div class="container">
    <RouterView />
    <!-- <QuizzesView /> -->
  </div>
</template>

<style scoped>
.container {
  width: 100%;
  margin: auto;
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>
