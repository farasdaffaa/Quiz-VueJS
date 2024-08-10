<script setup>
import { RouterView } from 'vue-router';
</script>

<template>
  <main class="container">
    <RouterView />
  </main>
</template>

<style scoped>
main {
  max-width: 900px;
  margin: 0 auto;
}
</style>