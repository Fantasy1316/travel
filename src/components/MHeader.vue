<template>
  <header class="m-header">
    <a href="#">
      <div class="m-header--logo">Travel</div>
    </a>
    <div class="m-header--menu" :class="{ 'm-header--menu_active': props.modelValue }" @click="handleMenuLogoToggler"></div>
  </header>
</template>

<script setup lang="ts">
import { ref } from 'vue'

const props = defineProps({
  modelValue: {
    type: Boolean,
    default: false
  }
})

const emits = defineEmits(['update:modelValue'])

const handleMenuLogoToggler = () => {
  emits('update:modelValue', !props.modelValue)
}

const menuActive = ref(false)
</script>

<style lang="scss" scoped>
.m-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  width: 100%;
  padding: $--screen-desktop-padding-top-bottom $--screen-desktop-padding-left-right;
  color: $--main-text-color;
  transition: 0.5s;

  a {
    color: $--main-text-color;
    text-decoration: none;
    transition: 0.3s;
  }

  a:hover {
    transform: scale(1.2);
    text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.5);
  }

  &--menu {
    width: $--header-toggle-width;
    height: $--header-toggle-width;
    background: url('../assets/svg/menu-line.svg') no-repeat center;
    background-size: $--header-toggle-width;
    filter: invert(1);

    &:hover {
      border: 2px solid #000;
      border-radius: 50%;
      cursor: pointer;
      animation: menu_logo ease-in 1s infinite;
    }

    &_active {
      background: url('../assets/svg/close-fill.svg') no-repeat center;
      background-size: $--header-toggle-width;
    }
  }
}

@media (max-width: 1200px) {
  .m-header {
    padding: $--screen-pad-padding-top-bottom $--screen-pad-padding-left-right;

    &--menu {
      width: $--header-toggle-width;
      height: $--header-toggle-width;
      background-size: $--header-pad-toggle-width;
    }
  }
}

@keyframes menu_logo {
  from,
  to {
    filter: invert(1);
    transform: scale(1);
  }
  50% {
    transform: scale(1.2);
  }
} ;
</style>
