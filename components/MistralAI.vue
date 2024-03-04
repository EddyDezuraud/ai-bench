<template>
    <button
      :class="$style.button"
      :style="{ backgroundColor: buttonColor }"
      @click="$emit('click')"
    >
      {{ label }}
    </button>
  </template>
  
  <script lang="ts" setup>
  import { ref, computed, watch } from 'vue';
  
  const props = defineProps<{
    label: string;
  }>();
  
  const buttonColor = ref('');
  
  const generateColor = (str: string) => {
    let hash = 0;
    for (let i = 0; i < str.length; i++) {
      hash = str.charCodeAt(i) + ((hash << 5) - hash);
    }
    let color = '#';
    for (let i = 0; i < 3; i++) {
      const value = (hash >> (i * 8)) & 0xff;
      color += `00${value.toString(16)}`.slice(-2);
    }
    return color;
  };
  
  const isContrastSufficient = (hexcolor: string) => {
    const r = parseInt(hexcolor.substr(0, 2), 16);
    const g = parseInt(hexcolor.substr(2, 2), 16);
    const b = parseInt(hexcolor.substr(4, 2), 16);
    const yiq = ((r * 299) + (g * 587) + (b * 114)) / 1000;
    return yiq >= 128;
  };
  
  const updateButtonColor = () => {
    let color = generateColor(props.label);
    while (!isContrastSufficient(color)) {
      color = generateColor(props.label + Math.random().toString(36).substring(7));
    }
    buttonColor.value = color;
  };
  
  watch(() => props.label, updateButtonColor);
  
  updateButtonColor();
  </script>
  
  <style module>
  .button {
    border-radius: 5px;
    color: white;
    padding: 5px 10px;
    border: none;
    cursor: pointer;
    transition: background-color 0.1s;
  }
  </style>
  