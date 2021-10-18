<template>
  <div class="main-container">
    <div class="container">
      <div class="box"></div>
      <div class="box"></div>
      <div class="box"></div>
      <div class="box"></div>
      <div class="box"></div>
      <div class="box"></div>
    </div>
    <btn-play @click="onPlay" />
  </div>
</template>

<script>
import { animate, stagger } from 'motion'
import BtnPlay from './BtnPlay.vue'
let animation
export default {
  components: {
    BtnPlay,
  },
  data() {
    return {
      isAnimating: false,
    }
  },
  methods: {
    onPlay() {
      if (this.isAnimating) {
        animation.cancel()
        this.isAnimating = false
        return
      }

      this.isAnimating = true
      animation = animate(
        '.box',
        { y: -40, rotate: 10 },
        {
          delay: stagger(0.1),
          repeat: Infinity,
          duration: 0.5,
          direction: 'alternate',
          easing: 'ease-in-out',
        }
      )
    },
  },
}
</script>

<style scoped>
section {
  margin-top: 200px;
  align-items: center;
  display: flex;
}
.container {
  align-items: center;
  display: flex;
}
.box {
  width: 50px;
  height: 50px;
  background: #44bba4;
  margin-right: 4px;
}
img {
  width: 200px;
}
</style>
