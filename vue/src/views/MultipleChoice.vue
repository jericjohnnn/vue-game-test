<template>
    <div>
      <p>{{ question.questionText }}</p>
      <div v-for="(option, index) in question.options" :key="index">
        <input
          type="radio"
          :id="`option-${index}`"
          :name="`question-${question.id}`"
          :value="option"
          v-model="selectedOption"
          @change="handleOptionChange"
        />
        <label :for="`option-${index}`">{{ option }}</label>
      </div>
    </div>
  </template>
  
  <script setup>
import { ref, defineProps, defineEmits } from 'vue'

const props = defineProps({
  question: Object
})

const emit = defineEmits(['answered'])

const selectedOption = ref('')

function handleOptionChange() {
  emit('answered', props.question.id, selectedOption.value)
}
</script>