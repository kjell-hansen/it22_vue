<script setup>
const props = defineProps(['active'])
const emits = defineEmits(['toggle-menu'])

function toggleActive() {
    emits('toggle-menu', props.active)
}
</script>
<template>
    <div id="burger" :class="{ 'active': props.active }" @click="toggleActive">
        <button type="button" class="burger-button" title="Menu">
            <span class="burger-bar bar--1"></span>
            <span class="burger-bar bar--2"></span>
            <span class="burger-bar bar--3"></span>
        </button>
    </div>
    <nav class="navbar" v-show="props.active">
        <RouterLink to="/">Home</RouterLink>
        <RouterLink to="/locations">Locations</RouterLink>
    </nav>
</template>
<style scoped>
#burger {
    display: block;
}

.burger-button {
    position: relative;
    height: 30px;
    width: 40px;
    display: block;
    z-index: 99;
    border: 0;
    border-radius: 0;
    background-color: transparent;
    pointer-events: all;
    transition: transform .6s cubic-bezier(.165, .84, .44, 1);
}

.burger-bar {
    background-color: #ed1313;
    position: absolute;
    top: 50%;
    right: 6px;
    left: 6px;
    height: 3px;
    width: auto;
    margin-top: -1px;
    transition: transform .6s cubic-bezier(.165, .84, .44, 1), opacity .3s cubic-bezier(.165, .84, .44, 1), background-color .6s cubic-bezier(.165, .84, .44, 1);

}

.bar--1 {
    transform: translateY(-6px);
    top: 40%;
}

.bar--2 {
    transform-origin: 100% 50%;
    transform: scaleX(1);
}

.bar--3 {
    transform: translateY(6px);
    top: 60%;
}

button {
    cursor: pointer;
}

#burger.active .burger-button {
    transform: rotate(-180deg);
}

#burger.active .bar--1 {
    transform: rotate(45deg);
    top: 50%;
}

#burger.active .bar--2 {
    opacity: 0;
}

#burger.active .bar--3 {
    transform: rotate(-45deg);
    top: 50%;
}
</style>