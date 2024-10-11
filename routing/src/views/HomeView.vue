<script setup>
import { inject, onMounted, ref } from 'vue';


const tid = ref(new Date().toLocaleString())
const views = inject('HomeViews')
onMounted(() => {
    views.value++
})
</script>

<template>
    <main>
        <p>
            När sidan laddades var klockan...<br>
            {{ tid }}
        </p>
        <p>
            Denna sidan har visats:
            <b>{{ views }}</b> gånger
        </p>
        <ul>
            <li>
                <a href="/my">Min sida</a>
            </li>
            <li>
                <RouterLink to="/my">Min sida</RouterLink>
            </li>
        </ul>
    </main>
</template>
