<script setup>
import q from '../assets/data/quizzes.json'
import { ref, watch } from 'vue'
import CardComponent from '../components/CardComponent.vue'
import HeaderMain from '@/components/HeaderMain.vue'

const quizzes = ref(q)
const search = ref('')

watch(search, () => {
  quizzes.value = q.filter((quiz) => quiz.name.toLowerCase().includes(search.value.toLowerCase()))
})
</script>

<template>
  <div>
    <HeaderMain />
    <div class="main-container">
      <header>
        <h1>Quizzes</h1>
        <input class="search-input" v-model.trim="search" type="text" placeholder="Search..." />
      </header>
      <div class="options-container">
        <CardComponent :quiz="quiz" v-for="quiz in quizzes" :key="quiz.id" class="card" />
      </div>
    </div>
  </div>
</template>

<style scoped>
.search-input {
  width: 55%;
  height: 25px;
  border: 1px solid rgb(183, 183, 183);
  padding: 0.5rem;
  border-radius: 0.2rem;
}
.main-container {
  width: 80%;
  margin: auto;
}
header {
  margin: bottom 10px;
  margin-top: 30px;
  display: flex;
  align-items: center;
  justify-content: center;
}

header h1 {
  font-weight: bold;
  margin-right: 30px;
}

.options-container {
  display: flex;
  flex-wrap: wrap;
  width: 100%;
  margin: 40px auto;

  justify-content: center;
}
.card {
  transition: transform 0.3s ease;
}

.card:hover {
  transform: scale(1.04);
}
</style>
