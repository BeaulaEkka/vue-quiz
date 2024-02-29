<script setup>
const { question } = defineProps(['question'])
const emit = defineEmits(['selectOption'])

const emitSelectedOption = (isCorrect) => {
  emit('selectOption', isCorrect)
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
        @click="emitSelectedOption(option.isCorrect)"
      >
        <p class="option-label">{{ option.label }}</p>
        <p class="option-value">{{ option.text }}</p>
      </div>
    </div>
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
  background-color: bisque;
  display: flex;
}

.option-value {
  background-color: rgb(244, 239, 239);
  font-size: 30px;
  padding-left: 20px;
  width: 100%;
  display: flex;
  align-items: center;
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
  }

  .option-value {
    font-size: 18px;
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
}
</style>
