<script setup>
const { questionStatus, barpercentage } = defineProps(['questionStatus', 'barpercentage'])
</script>

<template>
  <header>
    <h4>Question {{ questionStatus }}</h4>
    <div class="bar">
      <div class="completion" :style="{ width: barpercentage }"></div>
    </div>
  </header>
</template>

<style scoped>
header {
  margin-top: 20px;
  font-size: 30px;
}
.bar {
  height: 10px;
  width: 100%;
  border: 1px solid #f6c7eb;
  border-radius: 0.5rem;
}
.completion {
  height: 100%;
  width: 0%;
  background-color: #ffd8f6;
}
@media only screen and (max-width: 600px) {
  .bar {
    width: 95%;
  }
}

@media only screen and (min-width: 601px) and (max-width: 1024px) {
  .bar {
    width: 95%;
  }
}
</style>
