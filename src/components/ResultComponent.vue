<script setup>
const { numberOfCorrectAnswers, quizQuestionLength } = defineProps([
  'quizQuestionLength',
  'numberOfCorrectAnswers'
])
</script>

<template>
  <div class="results">
    <p>Your Results</p>
    <h1>{{ numberOfCorrectAnswers }} / {{ quizQuestionLength }}</h1>
    <RouterLink to="/">Go Back</RouterLink>
  </div>
</template>

<style scoped>
.results {
  text-align: center;
  padding: 100px 0;
}
p {
  font: 25px;
}
h1 {
  font: 80px;
}
</style>
