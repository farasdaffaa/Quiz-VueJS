<script setup>
import { ref, watch } from 'vue';
import srcQuiz from "../data/quizes.json";

import QuizCard from "../components/QuizCard.vue"

const quizes = ref(srcQuiz);
const search = ref("");

watch(search, () => {
  quizes.value = srcQuiz.filter((quiz) => {
    return quiz.title.toLowerCase().includes(search.value.toLowerCase());
  });
});

</script>

<template>
  <div>
    <header>
      <h1 id="title">QuizVue</h1>
      <input v-model.trim="search" type="text" id="search-input">
    </header>

    <section id="quiz-container">
      <QuizCard v-for="quiz in quizes" :key="quiz.id" v-bind:quiz="quiz" />
    </section>
</div>
</template>


<style scoped>
header {
  margin-top: 30px;
  margin-bottom: 10px;
  display: flex;
  align-items: center;
}

#title {
  font-weight: bold;
  margin-right: 30px;
}

#search-input {
  border: none;
  border-radius: 5px;
  background-color: #c9c9c9a9;
  padding: 10px;
}

#quiz-container {
  display: flex;
  flex-wrap: wrap;
  margin-top: 20px;
}

</style>