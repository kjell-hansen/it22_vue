<script setup>
import { inject } from 'vue';

const views = inject('HomeViews')
</script>
<template>
    <div class="about">
        <h1>This is an about page</h1>
        <p>
            HomeView har visats
            <b>{{ views }}</b> gånger
        </p>
    </div>
</template>

<style></style>
