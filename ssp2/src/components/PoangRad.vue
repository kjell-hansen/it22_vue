<script setup>
import { useGamesStore } from '@/stores/gameStore';
import { storeToRefs } from 'pinia';


const { score } = storeToRefs(useGamesStore())
</script>
<template>
  <p class="poangrad">
    <span>{{ score.user }}</span>
    -
    <span>{{ score.computer }}</span>
  </p>
</template>
<style scoped>
.poangrad {
  font-size: 1.5rem;
  font-weight: bold;
  text-align: center;
}
</style>
