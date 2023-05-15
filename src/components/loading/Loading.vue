<template> 
<svg class="loading" v-show="store.state.isLoading" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" style="margin: auto; background: rgba(0, 0, 0, .5); display: block;" width="100vw" height="100vh" viewBox="0 0 100 100" preserveAspectRatio="xMidYMid">
<circle cx="50" cy="50" fill="none" stroke="#0cdbe6" stroke-width="1" r="23" stroke-dasharray="108.38494654884786 38.12831551628262">
  <animateTransform attributeName="transform" type="rotate" repeatCount="indefinite" dur="0.7462686567164178s" values="0 50 50;360 50 50" keyTimes="0;1"></animateTransform>
</circle>
</svg>
</template>

<script setup>
import { useStore } from "vuex"

const store =  useStore()
</script>

<style lang="scss" >
.loading {
    position: fixed;
    left: 0;
    top: 0;
    bottom: 0;
    right: 0;
    z-index: 9; 
}
</style>