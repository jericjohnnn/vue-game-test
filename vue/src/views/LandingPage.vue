<template>
    <div class="landing-page" :style="{ backgroundColor: backgroundColor }">
      <img :src="imageUrl" alt="Landing page image" class="landing-image">
      <h1>{{ heading }}</h1>
      <h2>{{ subheading }}</h2>
      <button @click="goToMechanics">{{ buttonText }}</button>
    </div>
  </template>
  
  <script setup>
  import { ref } from 'vue'
  import { useRouter } from 'vue-router'

  const router = useRouter()
  
  const backgroundColor = ref('#00ffff')
  const imageUrl = ref('https://example.com/image.jpg')
  const heading = ref('Welcome to Our Website')
  const subheading = ref('Discover amazing features and services')
  const buttonText = ref('Get Started')

  const goToMechanics = () => {
  router.push('/mechanics')
}
  </script>
  
  <style scoped>
  .landing-page {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    height: 100vh;
    text-align: center;
  }
  
  .landing-image {
    max-width: 100%;
    height: auto;
    margin-bottom: 20px;
  }
  
  h1 {
    font-size: 2.5em;
    margin-bottom: 10px;
  }
  
  h2 {
    font-size: 1.5em;
    margin-bottom: 20px;
  }
  
  button {
    padding: 10px 20px;
    font-size: 1em;
    cursor: pointer;
  }
  </style>