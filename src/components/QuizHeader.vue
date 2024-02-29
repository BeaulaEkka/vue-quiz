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
  height: 30px;
  width: 300px;
  border: 1px solid bisque;
}
.completion {
  height: 100%;
  width: 0%;
  background-color: bisque;
}
</style>
