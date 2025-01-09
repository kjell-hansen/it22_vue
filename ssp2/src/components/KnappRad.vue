<script setup>
import { useGamesStore } from '@/stores/gameStore';
import { storeToRefs } from 'pinia';
import { watch } from 'vue';


const { alternatives, computerChoise, reset } = storeToRefs(useGamesStore())

function setUserChoise(e) {
  for (const button of document.querySelectorAll('button')) {
    button.classList.remove('selected')
  }
  e.target.classList.add('selected')
  let index = alternatives.value.indexOf(e.target.innerText)
  useGamesStore().userChoise(index)
}

watch(computerChoise, () => {
  for (const button of document.querySelectorAll('button')) {
    button.classList.remove('computer')
  }
  if (computerChoise.value > -1) {
    let text = alternatives.value[computerChoise.value]
    for (const button of document.querySelectorAll('button')) {
      if (button.innerText === text) {
        button.classList.add('computer')
      }
    }
  }
})

watch(reset, () => {
  if (reset.value) {
    for (const button of document.querySelectorAll('button')) {
      button.classList.remove('selected')
      button.classList.remove('computer')
    }
  }
})
</script>
<template>
  <div class="knapprad">
    <button v-for="knapp in alternatives" :key="knapp" @click="setUserChoise">{{ knapp }}</button>
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

.selected {
  background-color: pink;
}

.computer {
  border: 2px solid red;
}
</style>
