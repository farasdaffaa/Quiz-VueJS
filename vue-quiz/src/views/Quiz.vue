<script setup>
import QuizContent from '@/components/QuizContent.vue';
import QuizHeader from '@/components/QuizHeader.vue';
import QuizResult from '@/components/QuizResult.vue'

import { ref, watch, computed } from 'vue';
import { useRoute } from 'vue-router';
import quizes from "../data/quizes.json";

const route = useRoute();
const quizId = parseInt(route.params.id)
const quiz = quizes.find((q) => q.id === quizId)

const numberOfCorrectAnswers = ref(0)
const currentQuestionIndex = ref(0);
const showResult = ref(false);

const questionPage = computed(() => {
    return `${currentQuestionIndex.value +1} / ${quiz.questions.length}`
});

const barPercentage = computed(() => {
    return `${((currentQuestionIndex.value+1) / quiz.questions.length) * 100}%`
})

function onSelectOption(option) {
    if (option.correct) {
        numberOfCorrectAnswers.value++
    }

    if (currentQuestionIndex.value === quiz.questions.length -1) {
        showResult.value = true;
        return;
    }
    currentQuestionIndex.value++
}

// const questionPage = ref(`${currentQuestionIndex.value +1} / ${quiz.questions.length}`);

// watch(
//     () => currentQuestionIndex.value,
//     () => {
//         questionPage.value = `${currentQuestionIndex.value +1} / ${quiz.questions.length}`;
//     }
// ) 
const quizQuestionsLength = quiz.questions.length
</script>

<template>
    <div>
        <QuizHeader :questionPage="questionPage" :barPercentage="barPercentage" />

        <QuizContent v-if="!showResult" :question="quiz.questions[currentQuestionIndex]" @selectOption="onSelectOption" />

        <QuizResult v-else :quizQuestionsLength="quizQuestionsLength" :numberOfCorrectAnswers="numberOfCorrectAnswers" />

        <button @click="currentQuestionIndex++" :disabled="currentQuestionIndex === quiz.questions.length - 1">Next</button>

        
    </div>
</template>

<style scoped>



</style>