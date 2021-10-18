<template>
  <div class="main-container">
    <div class="container">
      <div class="easing-box easing-box-1"></div>
      <div class="easing-box easing-box-2"></div>
      <div class="easing-box easing-box-3"></div>
      <div class="easing-box easing-box-4"></div>
    </div>
    <btn-play @click="onPlay" />
  </div>
</template>

<script>
import { animate } from 'motion'
import BtnPlay from './BtnPlay.vue'
let animation = []

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
        animation.forEach(a => a && a.cancel())
        animation = []
        this.isAnimating = false
        return
      }

      this.isAnimating = true
      animation.push(
        animate(
          '.easing-box-1',
          { x: 100 },
          {
            duration: 1,
            repeat: Infinity,
            direction: 'alternate',
            easing: 'linear',
          }
        )
      )

      animation.push(
        animate(
          '.easing-box-2',
          { x: 100 },
          {
            duration: 1,
            repeat: Infinity,
            direction: 'alternate',
            easing: 'ease',
          }
        )
      )

      animation.push(
        animate(
          '.easing-box-3',
          { x: 100 },
          {
            duration: 1,
            repeat: Infinity,
            direction: 'alternate',
            easing: 'ease-in',
          }
        )
      )

      animation.push(
        animate(
          '.easing-box-4',
          { x: 100 },
          {
            duration: 1,
            repeat: Infinity,
            direction: 'alternate',
            easing: 'ease-in-out',
          }
        )
      )
    },
  },
}
</script>

<style scoped>
section {
  align-items: center;
  display: flex;
}
.container {
  margin: 1rem;
}
.easing-box {
  width: 50px;
  height: 50px;
  background: #44bba4;
  margin-bottom: 4px;
}
</style>
