<script setup>
import { defineProps } from 'vue';
import { RouterLink } from 'vue-router';

const { quizQuestionsLength, numberOfCorrectAnswers } = defineProps(["quizQuestionsLength", "numberOfCorrectAnswers"])
</script>


<template>
    <section class="results">
        <p>Score :</p>
        <h1>{{ numberOfCorrectAnswers }} / {{ quizQuestionsLength }}</h1>
        <RouterLink to="/">Go Back</RouterLink>
    </section>
</template>


<style scoped>
.results {
    text-align: center;
    padding: 100px 0;
}

p {
    font-size: 25px;
}

h1 {
    font-size: 80px;
}
</style>