<template>
    <button :style="style">{{ text }}</button>
</template>

<script setup>
defineProps(["text", "style"])
</script>

<style lang="scss" scoped>
button {
    background: #8D64DC;
    border-radius: 9.48718px;
    font-family: 'Jost';
    font-style: normal;
    font-weight: 600;
    font-size: 17.0769px;
    letter-spacing: 0.05em;
    color: #FFFFFF;
}
</style>