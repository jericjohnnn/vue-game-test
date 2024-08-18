<template>
    <div>
    <h1>hello</h1>
    <div v-if="answers">
        <h2>Your Answers:</h2>
        <ul>
          <li v-for="(answer, questionId) in answers" :key="questionId">
            Question {{ questionId }}: {{ answer }}
          </li>
        </ul>
      </div>
      
      <div v-if="quizData">
        <h2>Quiz Data:</h2>
        <pre>{{ JSON.stringify(quizData, null, 2) }}</pre>
      </div>
    </div>
  </template>
  
  <script setup>
import { ref, onMounted } from 'vue'
import { useRouter, useRoute } from 'vue-router';

const route = useRoute()
// const answers = ref(null)
const answers = route.state.answers;
// const quizData = ref(null)
const quizData = route.state.quizData;

onMounted(() => {
  if (route.params.state) {
    answers.value = route.params.state.answers
    quizData.value = route.params.state.quizData
  }

  console.log('Answers:', answers.value)
  console.log('Quiz Data:', quizData.value)

  // Use answers.value and quizData.value as needed
})




console.log('Received Answers:', answers);
console.log('Received Quiz Data:', quizData);
</script>
 
  