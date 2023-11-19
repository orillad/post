<template>
    <div class="post-item">
      <span class="emoji">{{ post.emoji }}</span>
      <div class="content">
        <p class="body">{{ post.body }}</p>
        <p class="created-at">Created at: {{ post.dataCreacio }}</p>
        <p class="user">User: {{ post.userId }}</p>
      </div>
    </div>
  </template>
  
  <script setup lang="ts">
  import { ref } from 'vue';
  
  // Props
  const props = defineProps(['post']);
  
  // Data
  </script>
  
  <style scoped>
  .post-item {
    border: 1px solid #ccc;
    padding: 10px;
    margin: 10px;
    display: flex;
    align-items: center;
  }
  
  .emoji {
    font-size: 1.5em;
    margin-right: 10px;
  }
  
  .content {
    flex: 1;
  }
  
  .body {
    margin-bottom: 5px;
  }
  
  .created-at,
  .user {
    font-style: italic;
    color: #888;
  }
  </style>
  