<template>
    <h2>Form</h2>
    <form @submit.prevent="gestionarSubmit">
      <textarea v-model="body" class="textarea" style="resize: none;" name="post" cols="60" maxlength="280" rows="7"
                @input="countChar"></textarea>
      <br>
      <p class="counter" :style="{ color: body.length === 280 ? 'red' : '' }">{{ `${body.length}/280` }}</p>
      <Emoticonos v-model="emoji"></Emoticonos>
  
      <button type="submit">Remember</button>
    </form>
  </template>
  
  <script setup lang="ts">
  import { computed, ref, defineEmits } from 'vue';
  import Emoticonos from '@/components/Emoticonos.vue';
  import type Entry from "@/types/Entry.ts";
  import type Emoji from "@/types/Emoji.ts";
  
  const emit = defineEmits<{
    (e: "@create", entry: Entry): void
  }>();
  
  const body = ref("");
  const emoji = ref<Emoji | null>(null);
  
  function countChar() {
    return body.value.length;
  }
  
  const gestionarSubmit = () => {
    emit('@create', {
      body: body.value,
      emoji: emoji.value ? emoji.value.icon : null,
      dataCreacio: new Date(),
      userId: 1,
      id: Math.random()
    });
  };
  </script>
  