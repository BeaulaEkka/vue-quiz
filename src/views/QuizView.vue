<script setup>
import QuestionComponent from '../components/QuestionComponent.vue'
import { useRoute } from 'vue-router'
import quizzes from '../assets/data/quizzes.json'
import { ref, computed } from 'vue'
import Resultcomponent from '../components/ResultComponent.vue'
import QuizHeader from '../components/QuizHeader.vue'
import HeaderMain from '@/components/HeaderMain.vue'

const route = useRoute()
const quizId = parseInt(route.params.id)
const quiz = quizzes.find((q) => q.id === quizId)
const currentQuestionIndex = ref(0)
const numberOfCorrectAnswers = ref(0)
const showResults = ref(false)

const questionStatus = computed(() => {
  return `${currentQuestionIndex.value}/${quiz.questions.length}`
})
const barpercentage = computed(
  () => `${(currentQuestionIndex.value / quiz.questions.length) * 100}%`
)

const onOptionSelected = (isCorrect) => {
  if (isCorrect) {
    numberOfCorrectAnswers.value++
  }
  if (quiz.questions.length - 1 === currentQuestionIndex.value) {
    showResults.value = true
  }
  currentQuestionIndex.value++
}
</script>

<template>
  <div>
    <HeaderMain />
    <div class="questions-container">
      <QuizHeader :questionStatus="questionStatus" :barpercentage="barpercentage" />

      <QuestionComponent
        v-if="!showResults"
        :question="quiz.questions[currentQuestionIndex]"
        @selectOption="onOptionSelected"
      />

      <Resultcomponent
        v-else
        :quizQuestionLength="quiz.questions.length"
        :numberOfCorrectAnswers="numberOfCorrectAnswers"
      />
    </div>
  </div>
</template>

<style scoped>
.questions-container {
  width: 60%;
  margin: auto;
}
@media only screen and (max-width: 400px) {
  .questions-container {
    width: 90%;
  }
}
@media only screen and (min-width: 601px) and (max-width: 1024px) {
  .questions-container {
    width: 80%;
  }
}
</style>
