<template>
  <footer class="m-footer">
    <a href="#"><img src="../assets/svg/facebook-fill.svg" class="m-footer--item" alt="facebook" /></a>
    <a href="#"><img src="../assets/svg/instagram-fill.svg" class="m-footer--item" alt="instagram" /></a>
    <a href="#"><img src="../assets/svg/twitter-fill.svg" class="m-footer--item" alt="twitter" /></a>
  </footer>
</template>

<script setup lang="ts"></script>

<style lang="scss" scoped>
.m-footer {
  display: flex;
  align-items: center;
  width: 100%;
  padding: $--screen-desktop-padding-top-bottom $--screen-desktop-padding-left-right;
  color: $--main-text-color;
  transition: 0.5s;

  a {
    &:not(:last-child) {
      margin-right: $--footer-margin-right;
    }
  }

  &--item {
    width: $--footer-icon-width;
    filter: invert(1);
    transition: 0.5s;

    &:hover {
      transform: translateY(-6px);
    }
  }
}

@media (max-width: 1200px) {
  .m-footer {
    padding: $--screen-pad-padding-top-bottom $--screen-pad-padding-left-right;

    &--item {
      width: $--footer-pad-icon-width;
    }
  }
}
</style>
