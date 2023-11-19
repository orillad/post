<script setup lang="ts">
import Formulari from "./components/Formulari.vue";
import Enviat from "./components/Enviat.vue"
import type Entry from "./types/Entry";
import { reactive } from "vue";

const entrades: Entry[] = reactive ([])

const manipularPost = (entradaPost: Entry) => {
  entrades.push(entradaPost)
  console.log(entradaPost)
}

</script>

<template>
  <div class="principal">
    <Formulari @@create="manipularPost"></Formulari>
  </div>
  <ul>
    <li v-for="entrada in entrades" :key="entrada.id">      
      <Enviat :post="entrada"></Enviat>
    </li>
  </ul>
</template>

<style scoped>
.principal{
  width: 800px;
}
</style>
