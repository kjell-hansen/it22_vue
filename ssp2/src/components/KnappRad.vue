<script setup>
import { useGamesStore } from '@/stores/gameStore';
import { storeToRefs } from 'pinia';


const { alternatives } = storeToRefs(useGamesStore())
</script>
<template>
  <div class="knapprad">
    <button v-for="knapp in alternatives" :key="knapp">{{ knapp }}</button>
  </div>
</template>
<style scoped>
.knapprad {
  display: flex;
  gap: 1rem;
  justify-content: center;
}

button {
  font-size: 1rem;
}
</style>
