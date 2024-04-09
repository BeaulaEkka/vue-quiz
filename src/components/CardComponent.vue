<script setup>
import { useRouter } from 'vue-router'

const { quiz } = defineProps(['quiz'])
const router = useRouter()
const navigateToQuiz = () => {
  router.push(`/quiz/${quiz.id}`)
}
</script>

<template>
  <div class="card" @click="navigateToQuiz">
    <img :src="quiz.img" alt="math pic" />
    <div class="card-text">
      <h2>{{ quiz.name }}</h2>
      <div class="card_sub_text">
        <p>{{ quiz.questions.length }} Questions</p>
        <p>Quiz</p>
      </div>
    </div>
  </div>
</template>

<style scoped>
.card {
  width: 310px;
  overflow: hidden;
  border-radius: 2%;
  box-shadow: 1px 1px 10px rgba(0, 0, 0, 0.1);
  margin-bottom: 35px;
  margin-right: 20px;
  cursor: pointer;
}
.card img {
  width: 100%;
  height: 190px;
  margin: 0;
  object-fit: cover;
}
.card_sub_text {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
}
.card .card-text {
  padding: 5px 15px;
}
.card .card-text p {
  color: rgb(163, 163, 163);
  font-size: medium;
}
.card .card-text h2 {
  font-weight: bold;
}
</style>
