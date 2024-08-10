<script setup>
import { defineProps } from 'vue';
import { useRouter } from 'vue-router';


const { quiz } = defineProps(["quiz"]);
const router = useRouter()

function goToQuiz() {
  router.push({name: "quiz", params: { id : quiz.id } })
}
</script>

<template>
    <div @click="goToQuiz" class="card">
        <img :src="quiz.img" :alt="quiz.title">
        <div class="card-body">
          <h2>{{ quiz.title }}</h2>
          <p>{{ quiz.questions.length }} Questions</p>
        </div>
      </div>
</template>

<style scoped>
.card {
  width: 270px;
  margin-right: 30px;
  margin-bottom: 30px;
  border-radius: 5px;
  overflow: hidden;
  box-shadow: 0 0 5px rgba(0, 0, 0, 0.1);
  cursor: pointer;
}
.card img {
  width: 100%;
  height: 200px;
  object-fit: cover;
  margin: 0;
}

.card-body {
  padding: 0 15px;
}
.card-body h2 {
  font-weight: bold;
}
</style>