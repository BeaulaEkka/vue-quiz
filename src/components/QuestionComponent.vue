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
        class="option"
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
.quesion {
  font-size: 40px;
  margin-bottom: 20px;
}
.option {
  display: flex;
  margin-bottom: 20px;
  cursor: pointer;
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
</style>
