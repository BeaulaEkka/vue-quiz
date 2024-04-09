<script setup>
import { useRouter } from 'vue-router'
const router = useRouter()
import { ref } from 'vue'

const hovering = ref(false)
</script>

<template>
  <nav>
    <div class="logo_container">
      <router-link to="/">
        <img src="../assets/images/logo2.png" width="100" />
      </router-link>
    </div>
  </nav>
</template>

<style scoped>
nav {
  display: flex;
  align-items: center;
  width: 100vw;
  height: 4rem;
  background-color: rgb(16, 52, 83);
}
.logo_container {
  width: 80%;
  margin: auto;
}
</style>
