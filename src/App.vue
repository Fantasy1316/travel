<template>
  <section class="main" :class="{ main_active: menuLogoActive }">
    <m-header v-model:modelValue="menuLogoActive"></m-header>
    <m-content v-model:modelValue="videoActive"></m-content>
    <m-footer></m-footer>
  </section>
  <section class="menu">
    <a href="#" class="menu-item" @click.navite="handleChangeVideo(0)"><span>spring</span></a>
    <a href="#" class="menu-item" @click.navite="handleChangeVideo(1)"><span>Summer</span></a>
    <a href="#" class="menu-item" @click.navite="handleChangeVideo(2)"><span>Auttom</span></a>
    <a href="#" class="menu-item" @click.navite="handleChangeVideo(3)"><span>Winter</span></a>
  </section>
</template>

<script setup lang="ts">
import MHeader from './components/MHeader.vue'
import MContent from './components/MContent.vue'
import MFooter from './components/MFooter.vue'
import { ref } from 'vue'

const menuLogoActive = ref(false)
const videoActive = ref(0)

const handleChangeVideo = (index: number) => {
  videoActive.value = index
}
</script>

<style lang="scss" scoped>
.main {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  align-items: center;
  max-width: $--main-desktop-max-width;
  width: 100%;
  height: 100vh;
  position: absolute;
  top: 0;
  right: 0;
  left: 0;
  bottom: 0;
  height: 100vh;
  user-select: none;
  z-index: 1;
  transform: perspective(5000px) translateX(0px) translateY(0) translateZ(0) rotateX(0) rotateY(0) rotateZ(0);
  overflow: hidden;
  transition: all 0.5s ease;

  &_active {
    position: absolute;
    top: $--main-desktop-left;
    right: $--menu-width;
    left: $--main-desktop-left;
    bottom: $--main-desktop-left;
    width: calc(100% - $--menu-width - $--main-desktop-left);
    height: calc(100vh - 2 * $--main-desktop-left);
    border-radius: 10px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.5);
    transform: perspective(5000px) translateX(0px) translateY(0) translateZ(0) rotateX(0) rotateY(30deg) rotateZ(0);
    overflow: hidden;
  }
}

.menu {
  position: absolute;
  top: 0;
  right: 0;
  bottom: 0;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  width: $--menu-width;

  &-item {
    display: inline-block;
    padding: 10px 30px;
    line-height: 1em;
    min-width: calc($--menu-width * 2 / 3);
    color: $--main-background-color;
    letter-spacing: 2px;
    border: 2px solid $--main-background-color;
    border-radius: 30px;
    text-align: center;
    text-decoration: none;
    text-transform: uppercase;
    box-shadow: 1px 1px 8px rgba(0, 0, 0, 0.1), -1px -1px 8px rgba(255, 255, 255, 0.1);
    transition: all 0.3s;

    &:not(:last-child) {
      margin-bottom: $--menu-margin-bottom;
    }

    &:hover {
      cursor: pointer;
      letter-spacing: 5px;
      color: $--main-text-color;
      background-color: $--main-background-color;
    }
  }
}

@media (max-width: 1200px) {
  .main,
  .menu {
    font-size: $--main-pad-font-size;
  }
}
</style>
