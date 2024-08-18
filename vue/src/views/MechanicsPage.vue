<template>
    <div class="mechanics-page" :style="backgroundStyle">
      <h1>{{ heading }}</h1>
      <div class="instruction">
        <img :src="instructionIcon" alt="Instruction icon" class="instruction-icon">
        <p>{{ instructionText }}</p>
      </div>
      <button @click="goToQuiz">{{ buttonText }}</button>
    </div>
  </template>
  
  <script setup>
  import { ref, computed } from 'vue'
  import { useRouter } from 'vue-router'

const router = useRouter()
  
  const backgroundColor = ref('#f0f0f0')
  const backgroundImage = ref('')
  const heading = ref('How It Works')
  const instructionIcon = ref('https://example.com/icon.png')
  const instructionText = ref('Follow these simple steps to get started.')
  const buttonText = ref('Begin Now')
  
  const backgroundStyle = computed(() => ({
    backgroundColor: backgroundColor.value,
    backgroundImage: backgroundImage.value ? `url(${backgroundImage.value})` : 'none',
    backgroundSize: 'cover',
    backgroundPosition: 'center'
  }))


  const goToQuiz = () => {
  router.push('/quiz')
}
  </script>
  
  <style scoped>
  .mechanics-page {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    height: 100vh;
    text-align: center;
    padding: 20px;
  }
  
  h1 {
    font-size: 2.5em;
    margin-bottom: 20px;
  }
  
  .instruction {
    display: flex;
    align-items: center;
    margin-bottom: 20px;
  }
  
  .instruction-icon {
    width: 50px;
    height: 50px;
    margin-right: 10px;
  }
  
  p {
    font-size: 1.2em;
  }
  
  button {
    padding: 10px 20px;
    font-size: 1em;
    cursor: pointer;
  }
  </style>