<script setup>
import { ref } from 'vue'
const { question } = defineProps(['question'])
const emit = defineEmits(['selectOption'])

const emitSelectedOption = (isCorrect) => {
  emit('selectOption', isCorrect)
}

const showFeedback = ref(false)
const feedback = ref('')
const checkAnswer = (option) => {
  if (!option.isCorrect) {
    showFeedback.value = true
    feedback.value =
      'Oh no, that was wrong. The correct answer is: ' +
      question.options.find((opt) => opt.isCorrect).text
  } else {
    showFeedback.value = true
    feedback.value = 'Correct!'
  }

  // Delay clearing the feedback after 1 second
  setTimeout(() => {
    showFeedback.value = false
    feedback.value = ''

    // Delay navigation to the next page after 1 second if feedback is cleared
    setTimeout(() => {
      // Navigate to the next page here
      // For example:
      // router.push('/next-page')
    }, 500)
  }, 500)
}
</script>

<template>
  <div class="question-section">
    <h1 class="question">{{ question.text }}</h1>
    <div class="options-container">
      <div
        class="option-box"
        v-for="option in question.options"
        :key="option.id"
        @click="
          () => {
            checkAnswer(option)
            emitSelectedOption(option.isCorrect)
          }
        "
      >
        <div class="option_box_individual">
          <p class="option-label">{{ option.label }}</p>
          <p class="option-value">{{ option.text }}</p>
        </div>
      </div>
    </div>
    <p v-if="showFeedback" class="feedback_box">{{ feedback }}</p>
  </div>
</template>

<style scoped>
.question-section {
  margin-top: 20px;
}
.question {
  font-size: 40px;
  margin-bottom: 20px;
}
.options-container {
  margin-top: 3rem;
  width: 100%;
}
.option-box {
  display: flex;
  cursor: pointer;
  margin: -3rem auto;
}
.option-label {
  width: 60px;
  height: 60px;
  font-size: 30px;
  justify-content: center;
  align-items: center;
  background-color: hsl(305, 67%, 83%);
  display: flex;
  border-top-left-radius: 0.5rem;
  border-bottom-left-radius: 0.5rem;
}

.option-value {
  background-color: hsl(27, 84%, 83%);
  font-size: 30px;
  padding-left: 20px;
  width: 100%;
  display: flex;
  align-items: center;
  border-bottom-right-radius: 0.5rem;
  border-top-right-radius: 0.5rem;
}
.feedback_box {
  margin: 2rem;
  color: lightgrey;
}
.option_box_individual {
  display: flex;
  width: 100%;
}
/* Media Queries for Mobile */
@media only screen and (max-width: 600px) {
  .question-section {
    width: 95%;
  }
  .question {
    font-size: 25px;
  }

  .option-label {
    font-size: 18px;
    margin-top: 1rem;
  }

  .option-value {
    font-size: 18px;
    margin-top: 1rem;
  }
  .option_box_individual {
    margin-bottom: 1rem;
  }
}
/* Media Queries for iPad */
@media only screen and (min-width: 601px) and (max-width: 1024px) {
  .question-section {
    width: 95%;
  }
  .question {
    font-size: 35px;
  }

  .option-label {
    font-size: 25px;
  }

  .option-value {
    font-size: 25px;
  }
  .option_box_individual {
    margin-bottom: 1rem;
  }
}
</style>
