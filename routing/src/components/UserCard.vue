<script setup>
const props = defineProps(['user'])
</script>
<template>
    <div class="card">
        <img :src="props.user.image">
        <div>
            <p>id: {{ props.user.id }}</p>
            <p>Name: {{ props.user.namn }}</p>
        </div>
    </div>
</template>
<style scoped>
.card {
    display: flex;
    flex-direction: row;
    background-color: aquamarine;
    max-width: 250px;
    border: 1px solid navy;
    box-shadow: 5px 5px 5px #a79dff;
}

p {
    margin-left: 1em;
}

img {
    height: 75px;
    padding: 3px;
}
</style>