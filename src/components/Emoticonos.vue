<template>
    <div>
      <h2>Select an emoji:</h2>
      <div class="emojis-container">
        <div
          v-for="emoji in emojis"
          :key="emoji.id"
          @click="selectEmoji(emoji)"
          :class="{ 'selected-emoji': isSelected(emoji) }"
          class="emoji"
        >
          {{ emoji.icon }}
        </div>
      </div>
    </div>
  </template>
  
  <script setup lang="ts">
  import { ref, defineProps, defineEmits } from 'vue';

  
  const { modelValue } = defineProps(['modelValue']);
  const emit = defineEmits();
  
  const emojis = ref([
    { id: 1, icon: '😊' },
    { id: 2, icon: '😍' },
    { id: 3, icon: '🥳' },
    { id: 4, icon: '🎉' },
  ]);
  
  const selectedEmoji = ref(null);
  
  const selectEmoji = (emoji: any) => {
    selectedEmoji.value = emoji;
    emit('update:modelValue', emoji);
  };
  
  const isSelected = (emoji: any) => {
    return emoji === selectedEmoji.value;
  };
  </script>
  
  <style scoped>
  .emojis-container {
    display: flex;
    justify-content: flex-start;
  }
  
  .emoji {
    font-size: 2em;
    cursor: pointer;
    margin-right: 10px;
  }
  
  .selected-emoji {
    border: 2px solid blue; /* You can customize the border style here */
  }
  </style>
  