<template>
  <div>
    <h1>{{ quizData.title }}</h1>
    <component v-for="(question, index) in quizData.questions" :key="question.id"
      v-show="index === currentQuestionIndex" :is="getComponentForType(question.type)" :question="question"
      @answered="handleAnswer" />
  </div>
</template>

<script setup>
import { ref } from 'vue'
import quiz from '../quiz.json';
import { useRouter } from 'vue-router'

const router = useRouter()

// Import question type components
import MultipleChoice from './MultipleChoice.vue'

const quizData = ref(quiz)

// Reactive variable to track the current question index
const currentQuestionIndex = ref(0)
const answers = ref({}) // New ref to store answers

// Function to return the component based on the question type
function getComponentForType(type) {
  switch (type) {
    case 'multipleChoice':
      return MultipleChoice
    // Add more cases for other question types as needed
    default:
      return null
  }
}

// Method to handle when a question is answered
function handleAnswer(questionId, selectedOption) {
  // Store the answer
  answers.value[questionId] = selectedOption

  // Log the current answer
  console.log(`Question ${questionId} answered:`, selectedOption)

  // Move to the next question
  if (currentQuestionIndex.value < quizData.value.questions.length - 1) {
    currentQuestionIndex.value++
  } else {

    // All questions answered, log the final results
    console.log('All questions answered. Final results:', answers.value)
  router.push({
      path: '/getResults',
      state: {
        answers: answers.value,
        quizData: quizData.value
      }
    });
    // logQuizResults()
  }
}

// function logQuizResults() {
//   const results = quizData.value.questions.map(question => ({
//     questionId: question.id,
//     questionText: question.questionText,
//     correctAnswer: question.answer,
//     userAnswer: answers.value[question.id],
//     isCorrect: answers.value[question.id] === question.answer
//   }))

//   console.log('Quiz Results:', results)
//   console.log('Total Correct:', results.filter(r => r.isCorrect).length)
//   console.log('Total Questions:', results.length)
// }
</script>