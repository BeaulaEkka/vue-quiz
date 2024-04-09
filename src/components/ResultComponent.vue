<script setup>
const { numberOfCorrectAnswers, quizQuestionLength } = defineProps([
  'quizQuestionLength',
  'numberOfCorrectAnswers'
])
</script>

<template>
  <div class="results">
    <h1 v-if="numberOfCorrectAnswers == quizQuestionLength">Congratulations, You are a genius!</h1>
    <h1 v-else>Your score is :</h1>
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
