<template>
  <div class="burger">
    <div :class="isActive ? 'burger-menu active' : 'burger-menu'" @click="isActive = !isActive">
      <div class="burger-line"></div>
      <div class="burger-line"></div>
      <div class="burger-line"></div>
    </div>
    <div :class="isActive ? 'burger-wrapper active' : 'burger-wrapper'">
      <ul class="burger-wrapper">
      </ul>
    </div>
  </div>
</template>

<script setup>
import { ref } from "vue";

const isActive = ref(false)
</script>

<style lang="scss">
.burger {
  display: none;

  &-menu {
    background: #fff;
    display: flex;
    flex-direction: column;
    gap: 5px;
    align-items: end;
    justify-content: center;
    width: 42px;
    height: 42px;
    border-radius: 10px;
    padding: 14px 13.8px 14.53px 9px;
    box-sizing: border-box;

    &.active {
      position: fixed;
      top: 21px;
      right: 20px;
      z-index: 2;
    }
  }

  &-line {
    background: #1EA9B9;
    height: 2px;
    border-radius: 2px;

    &:first-child {
      width: 12px;
    }

    &:nth-child(2) {
      width: 21px;
    }

    &:last-child {
      width: 16px;
    }
  }

  &-wrapper {
    width: 100%;
    height: 0%;
    background: aqua;
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    transition: .3s;

    &.active {
      height: 100%;
    }
  }
}

@media screen and (max-width:780px) {
  .burger {
    display: block;
  }
}
</style>