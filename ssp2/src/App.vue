<script setup>
import KnappRad from './components/KnappRad.vue';
import NollStall from './components/NollStall.vue';
import PoangRad from './components/PoangRad.vue';
import ResultatRad from './components/ResultatRad.vue';

</script>

<template>
  <header>
    <h1>Sten, sax, påse</h1>
    <p>Revisited</p>
  </header>
  <KnappRad />
  <ResultatRad />
  <PoangRad />
  <NollStall />
</template>

<style scoped>
header {
  line-height: 1.5;
}
</style>
