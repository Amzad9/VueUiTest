
 
  <script setup>
  import { defineProps, defineEmits } from 'vue';
  
  const { chips } = defineProps({
    chips: Object
  });
  
 defineEmits(["close"]);
  
  </script>
<template>
    <div class="mt-5">
      <div v-for="(chip, index) in chips" :key="index" class="inline-flex items-center space-x-3 bg-blue-700 text-white rounded-full px-3 py-2 me-2">
        <button type="button" @click="$emit('close', index)" class="flex items-center text-gray-100">
          <span>{{ chip.content }}</span>
          <svg class="h-5 w-5" fill="white" viewBox="0 0 20 20">
            <path fill-rule="evenodd" d="M5.293 5.293a1 1 0 011.414 0L10 8.586l3.293-3.293a1 1 0 111.414 1.414L11.414 10l3.293 3.293a1 1 0 01-1.414 1.414L10 11.414l-3.293 3.293a1 1 0 01-1.414-1.414L8.586 10 5.293 6.707a1 1 0 010-1.414z" clip-rule="evenodd" />
          </svg>
        </button>
      </div>
    </div>
  </template>
 
  