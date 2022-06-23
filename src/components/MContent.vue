<template>
  <div class="m-content">
    <video src="../assets/videos/spring.mp4" class="m-content--video" :class="{ 'm-content--video_active': props.modelValue === 0 }" autoplay muted loop></video>
    <video src="../assets/videos/summer.mp4" class="m-content--video" :class="{ 'm-content--video_active': props.modelValue === 1 }" autoplay muted loop></video>
    <video src="../assets/videos/autumn.mp4" class="m-content--video" :class="{ 'm-content--video_active': props.modelValue === 2 }" autoplay muted loop></video>
    <video src="../assets/videos/winter.mp4" class="m-content--video" :class="{ 'm-content--video_active': props.modelValue === 3 }" autoplay muted loop></video>
    <div
      class="m-content--overlay"
      :class="[
        { 'm-content--overlay_spring': props.modelValue === 0 },
        { 'm-content--overlay_summer': props.modelValue === 1 },
        { 'm-content--overlay_autumn': props.modelValue === 2 },
        { 'm-content--overlay_winter': props.modelValue === 3 }
      ]"
    ></div>

    <section class="m-content--text">
      <h1 class="text-title">{{ content[props.modelValue].title }}</h1>
      <h2 class="text-subtitle">{{ content[props.modelValue].subtitle }}</h2>
      <p class="text-desc">
        The world can be changed by man's endeavor, and that this endeavor can lead to something new and better .No man can sever the bonds that unite him to his society simply by averting his eyes.
      </p>
      <a href="#" class="text-btn">Explore</a>
    </section>
  </div>
</template>

<script setup lang="ts">
import { reactive } from 'vue'

const props = defineProps({
  modelValue: {
    type: Number,
    default: 0
  }
})

const content = reactive([
  {
    title: 'Spring',
    subtitle: 'Fell the new vitality'
  },
  {
    title: 'Summer',
    subtitle: 'Enjoy passionate time'
  },
  {
    title: 'Autumn',
    subtitle: 'Experience without limits'
  },
  {
    title: 'Winter',
    subtitle: 'Enjoy peace and freedom'
  }
])
</script>

<style lang="scss" scoped>
.m-content {
  width: 100%;
  padding: $--screen-desktop-padding-top-bottom $--screen-desktop-padding-left-right;
  color: $--main-text-color;
  transition: 0.5s;

  &--video,
  &--overlay {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    z-index: -1;
    transition: 1s;
  }

  &--video {
    margin: 0;
    padding: 0;
    clip-path: ellipse(0% 0% at 0% 50%);
    object-fit: cover;

    &_active {
      clip-path: ellipse(150% 70% at 0% 50%);
    }
  }

  &--overlay {
    mix-blend-mode: overlay;

    &_spring {
      background: $--video-overlay-spring-color;
    }

    &_summer {
      background: $--video-overlay-summer-color;
    }

    &_autumn {
      background: $--video-overlay-autumn-color;
    }

    &_winter {
      background: $--video-overlay-winter-color;
    }
  }

  &--text {
    position: relative;
    z-index: 1;

    .text-title,
    .text-subtitle,
    .text-desc {
      padding: 0;
      margin: 0;
    }

    .text-title,
    .text-subtitle {
      text-transform: uppercase;
    }

    .text-title {
      font-size: $--text-desc-h1-desktop-size;
      line-height: 1em;
    }

    .text-subtitle {
      font-size: $--text-desc-h2-desktop-size;
      line-height: 1em;
    }

    .text-desc {
      max-width: 700px;
      min-width: 400px;
      line-height: 1.5em;
      margin: 3em 0;
      font-size: $--text-desc-p-desktop-size;
    }

    .text-btn {
      display: inline-block;
      padding: 10px 30px;
      line-height: 1em;
      font-size: $--text-desc-btn-desktop-size;
      color: $--main-text-color;
      letter-spacing: 2px;
      border: 2px solid $--main-text-color;
      border-radius: 30px;
      text-decoration: none;
      text-transform: uppercase;
      box-shadow: 1px 1px 8px rgba(0, 0, 0, 0.1), -1px -1px 8px rgba(255, 255, 255, 0.1);
      transition: all 0.3s;

      &:hover {
        letter-spacing: 5px;
        color: $--main-text-color;
        background-color: $--main-background-color;
      }
    }
  }
}

@media (max-width: 1200px) {
  .m-content {
    padding: $--screen-pad-padding-top-bottom $--screen-pad-padding-left-right;

    &--text {
      .text-title {
        font-size: $--text-desc-h1-pad-size;
      }

      .text-subtitle {
        font-size: $--text-desc-h2-pad-size;
      }

      .text-desc {
        max-width: 500px;
        min-width: 300px;
        font-size: $--text-desc-p-pad-size;
      }
    }
  }
}
</style>
