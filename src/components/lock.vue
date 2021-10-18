<template>
  <div class="main-container">
    <svg xmlns="http://www.w3.org/2000/svg" width="53" height="53" viewBox="0 0 53 53" fill="none">
      <g id="lock">
        <g id="bg">
          <path
            id="Vector"
            d="M26.3031 0.374512C40.6097 0.374512 52.2256 11.9904 52.2256 26.297C52.2256 40.6036 40.6097 52.2195 26.3031 52.2195C11.9965 52.2195 0.380615 40.6036 0.380615 26.297C0.380615 11.9904 11.9965 0.374512 26.3031 0.374512Z"
            fill="#A3A3A3"
          />
        </g>
        <g id="pad-lock">
          <g id="body-lock">
            <path
              id="Vector_2"
              d="M34.496 26.625V34.833C34.496 35.9368 33.5998 36.833 32.496 36.833H20.375C19.2712 36.833 18.375 35.9368 18.375 34.833V26.625C18.375 25.5212 19.2712 24.625 20.375 24.625H32.496C33.5998 24.625 34.496 25.5212 34.496 26.625Z"
              fill="white"
            />
            <path
              id="Vector_3"
              d="M27.5 31.75V32.75C27.5 33.3019 27.0519 33.75 26.5 33.75C25.9481 33.75 25.5 33.3019 25.5 32.75V31.75C25.5 31.1981 25.9481 30.75 26.5 30.75C27.0519 30.75 27.5 31.1981 27.5 31.75ZM28.5 29.75C28.5 30.8538 27.6038 31.75 26.5 31.75C25.3962 31.75 24.5 30.8538 24.5 29.75C24.5 28.6462 25.3962 27.75 26.5 27.75C27.6038 27.75 28.5 28.6462 28.5 29.75Z"
              fill="#A3A3A3"
            />
          </g>
          <path
            pathLength="1"
            id="head-lock"
            d="M21.8751 25.375C21.8751 25.375 20.6871 17.812 26.3751 17.812C32.0361 17.812 31.2593 25.1356 31.2593 25.1356"
            stroke="white"
            stroke-width="3"
            stroke-linecap="round"
          />
        </g>

        <g id="lock_icon">
          <path
            id="Vector_5"
            d="M37.7454 19.4505C36.4778 17.4661 34.7292 15.8342 32.662 14.7065C30.5949 13.5788 28.2763 12.9918 25.9215 13.0001C18.2324 13.0001 12 19.1228 12 26.6762C12 34.2296 18.2339 40.3523 25.9244 40.3523C33.615 40.3523 39.8489 34.2296 39.8489 26.6762C39.8459 25.1654 39.5877 23.6659 39.0851 22.2412C39.8286 25.9919 36.55 30.4024 30.7868 31.7378C24.6944 33.1483 18.2916 30.9394 17.4225 27.1541C16.552 23.3701 22.513 18.99 27.3984 17.8711C31.8768 16.8461 35.5972 17.5578 37.6025 19.5083"
            fill="white"
          />
          <path
            id="Vector_6"
            fill-rule="evenodd"
            clip-rule="evenodd"
            d="M28.1205 26.3463L22.1277 23.3275C21.8606 23.0691 24.0377 25.558 28.1912 30.7929C28.4366 31.096 28.8697 31.0469 29.0718 30.764C37.2244 20.7159 41.3216 16.3054 39.6195 17.5311L28.1205 26.3477V26.3463Z"
            fill="white"
          />
        </g>
      </g>
    </svg>
    <btn-play @click="onPlay" />
  </div>
</template>

<script>
import { timeline } from 'motion'
import BtnPlay from './BtnPlay.vue'
let securedAnimation
let securingAnimation
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
        securedAnimation && securedAnimation.cancel()
        securingAnimation && securingAnimation.cancel()
        this.isAnimating = false
        return
      }

      this.isAnimating = true
      this.resetStyle('#pad-lock')
      this.resetStyle('#head-lock')
      this.resetStyle('#lock_icon')

      console.log(123)

      this.securing()
      setTimeout(() => {
        this.secured()
      }, 1500)
    },

    resetStyle(el, style = ['opacity', 'transform']) {
      const $el = document.querySelector(el)
      if ($el) {
        style.forEach(s => {
          $el.style[s] = null
        })
      }
    },

    securing() {
      const sequence = []
      sequence.push([
        '#pad-lock',
        {
          transform: ['rotate(-20deg)'],
        },
        { duration: 0.2, delay: 0.3 },
      ])

      sequence.push([
        '#pad-lock',
        {
          transform: ['rotate(20deg)'],
        },
        { duration: 0.2 },
      ])

      sequence.push([
        '#pad-lock',
        {
          transform: ['rotate(0)'],
        },
        { duration: 0.2 },
      ])
      securingAnimation = timeline(sequence, { repeat: 999999 })
    },
    secured() {
      setTimeout(() => {
        securingAnimation.finish()
        const sequence = []

        sequence.push([
          '#head-lock',
          {
            strokeDashoffset: 0,
          },
          { duration: 0.3, delay: 0.2 },
        ])
        sequence.push([
          '#pad-lock',
          {
            transform: ['rotate(30deg)'],
          },
          { duration: 0.35, delay: 0.2 },
        ])
        sequence.push([
          '#pad-lock',
          {
            transform: ['rotate(-360deg)'],
            opacity: 0,
          },
          { duration: 0.6 },
        ])

        sequence.push([
          '#lock_icon',
          {
            transform: ['rotate(-360deg)'],
            opacity: 1,
          },
          { duration: 0.6, at: '<' },
        ])

        securedAnimation = timeline(sequence)
      }, ((securingAnimation.currentTime % securingAnimation.duration) - securingAnimation.duration) * -1000)
    },
  },
}
</script>

<style scoped>
#pad-lock,
#lock_icon {
  transform-origin: center center;
  transform-box: fill-box;
}

#lock_icon {
  opacity: 0;
}

#head-lock {
  stroke-dasharray: 1;
  stroke-dashoffset: 1;
  stroke-dashoffset: 0.2;
}
</style>
