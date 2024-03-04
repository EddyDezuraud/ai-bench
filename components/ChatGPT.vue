<template>
    <button
      :class="$style.myClass"
      @click="$emit('click')"
      :style="{ backgroundColor: buttonBackgroundColor }"
    >
      {{ label }}
    </button>
  </template>
  
  <script setup lang="ts">
  import { ref, watch } from 'vue';
  
  const props = defineProps({
    label: {
      type: String,
      required: true
    }
  });
  
  const buttonBackgroundColor = ref<string>('');
  
  watch(() => props.label, (newValue) => {
    buttonBackgroundColor.value = generateBackgroundColor(newValue);
  });
  
  function generateBackgroundColor(label: string): string {
    const hash = hashCode(label);
    const hue = hash % 360;
    return `hsla(${hue}, 70%, 50%, 1)`;
  }
  
  function hashCode(str: string): number {
    let hash = 0;
    for (let i = 0; i < str.length; i++) {
      hash = str.charCodeAt(i) + ((hash << 5) - hash);
    }
    return hash;
  }
  </script>
  
  <style module>
  .myClass {
    border-radius: 10px;
    color: white;
    padding: 10px 20px;
    border: none;
    cursor: pointer;
    transition: background-color 0.1s ease-in-out;
  }
  </style>
  