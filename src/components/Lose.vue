<template>
  <div class="main-container">
    <svg
      xmlns="http://www.w3.org/2000/svg"
      width="1080"
      height="1080"
      viewBox="0 0 1080 1080"
      fill="none"
      style="width: 100%; height: 100%"
    >
      <g id="lose">
        <path
          id="Vector"
          d="M540 155C752.482 155 925 327.518 925 540C925 752.482 752.482 925 540 925C327.518 925 155 752.482 155 540C155 327.518 327.518 155 540 155Z"
          fill="#FFB81A"
        />
        <path
          id="mouth"
          d="M490.5 801.924C504.731 796.121 522.289 794.755 540.473 794.718C558.489 794.68 575.887 796.551 589.5 801.924C582.694 790.747 566.456 783.714 540 783.714C513.99 783.714 495.759 791.177 490.5 801.924Z"
          fill="black"
          stroke="black"
          stroke-width="15"
          stroke-linecap="round"
          stroke-linejoin="round"
        />
        <g id="eye-left">
          <path
            id="eye-brow-left"
            d="M459.921 446.166C410 493.748 338.936 482.046 338.936 482.046"
            stroke="black"
            stroke-width="30"
            stroke-linecap="round"
            stroke-linejoin="round"
          />
          <g id="eye-left">
            <path
              id="Vector_3"
              d="M418.2 501C467.319 501 507.2 540.881 507.2 590C507.2 639.119 467.319 679 418.2 679C369.081 679 329.2 639.119 329.2 590C329.2 540.881 369.081 501 418.2 501Z"
              fill="black"
            />
            <g id="eye-left-shade">
              <path
                id="Vector_4"
                d="M372.875 531.183C398.748 512.7 432.319 515.283 447.794 536.946C463.268 558.608 454.826 591.203 428.953 609.686C403.08 628.168 369.509 625.585 354.034 603.923C338.559 582.26 347.002 549.665 372.875 531.183Z"
                fill="white"
              />
              <path
                id="Vector_5"
                d="M449.724 622.397C456.512 622.397 462.022 627.908 462.022 634.695C462.022 641.482 456.512 646.993 449.724 646.993C442.937 646.993 437.427 641.482 437.427 634.695C437.427 627.908 442.937 622.397 449.724 622.397Z"
                fill="white"
              />
            </g>
          </g>
        </g>
        <g id="eye-right">
          <path
            id="eye-brow-right"
            d="M620.079 444.166C670 491.748 741.064 480.046 741.064 480.046"
            stroke="black"
            stroke-width="30"
            stroke-linecap="round"
            stroke-linejoin="round"
          />
          <g id="eye-right">
            <path
              id="eye-right-bg"
              d="M661.8 501C612.681 501 572.8 540.881 572.8 590C572.8 639.119 612.681 679 661.8 679C710.919 679 750.8 639.119 750.8 590C750.8 540.881 710.919 501 661.8 501Z"
              fill="black"
            />
            <g id="eye-right-shade">
              <path
                id="Vector_6"
                d="M614.874 531.183C640.747 512.7 674.318 515.283 689.793 536.946C705.268 558.608 696.825 591.203 670.952 609.686C645.079 628.168 611.508 625.585 596.033 603.923C580.558 582.26 589.001 549.665 614.874 531.183Z"
                fill="white"
              />
              <path
                id="Vector_7"
                d="M691.724 622.397C698.512 622.397 704.022 627.908 704.022 634.695C704.022 641.482 698.512 646.993 691.724 646.993C684.937 646.993 679.427 641.482 679.427 634.695C679.427 627.908 684.937 622.397 691.724 622.397Z"
                fill="white"
              />
            </g>
          </g>
        </g>
        <path
          id="tear"
          d="M714 663C714 663 719 672.011 719 675.172C719 678.332 716.761 680.894 714 680.894C711.239 680.894 709 678.332 709 675.172C709 672.011 714 663 714 663Z"
          fill="#2EB4FF"
        />
      </g>
    </svg>
    <btn-play @click="onPlay" />
  </div>
</template>

<script>
import { timeline, animate } from 'motion'
import BtnPlay from './BtnPlay.vue'
let mainTimeline
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
      this.initAnimation()
    },
    initAnimation() {
      if (this.isAnimating) {
        animation.forEach(a => a && a.cancel())
        mainTimeline && mainTimeline.cancel()
        animation = []
        this.isAnimating = false
        return
      }
      this.isAnimating = true

      const sequence = []

      animation.push(
        animate(
          '#eye-left-shade',
          {
            transform: 'translateX(-2px)',
          },
          {
            duration: 0.1,
            direction: 'alternate',
            repeat: Infinity,
          }
        )
      )

      animation.push(
        animate(
          '#eye-right-shade',
          {
            transform: 'translateX(-2px)',
          },
          {
            duration: 0.1,
            direction: 'alternate',
            repeat: Infinity,
          }
        )
      )

      sequence.push(
        [
          '#tear',
          {
            transform: 'translateY(-3px) scale(8)',
          },
          {
            duration: 1,
          },
        ],
        [
          '#eye-brow-left',
          {
            transform: 'translateY(-50px)',
          },
          {
            duration: 1,
            at: '<',
          },
        ],
        [
          '#eye-brow-left',
          {
            transform: 'translateY(-50px)',
          },
          {
            duration: 1,
            at: '<',
          },
        ],
        [
          '#eye-brow-right',
          {
            transform: 'translateY(-50px)',
          },
          {
            duration: 1,
            at: '<',
          },
        ],
        [
          '#eye-left',
          {
            transform: 'translateY(-30px)',
          },
          {
            duration: 1,
            at: '<',
          },
        ],
        [
          '#eye-right',
          {
            transform: 'translateY(-30px)',
          },
          {
            duration: 1,
            at: '<',
          },
        ],
        [
          '#mouth',
          {
            transform: 'translateY(-40px) scaleY(1.6)',
          },
          {
            duration: 1,
            at: '<',
          },
        ],
        [
          '#tear',
          {
            transform: 'translateY(300px) scale(0)',
            opacity: 0,
          },
          {
            duration: 1,
            easing: [0, 0.68, 0.25, 1.12],
          },
        ],

        [
          '#eye-brow-left',
          {
            transform: 'translateY(0)',
          },
          {
            duration: 1,
            at: '-.75',
          },
        ],
        [
          '#eye-brow-left',
          {
            transform: 'translateY(0)',
          },
          {
            duration: 1,
            at: '<',
          },
        ],
        [
          '#eye-brow-right',
          {
            transform: 'translateY(0)',
          },
          {
            duration: 1,
            at: '<',
          },
        ],
        [
          '#eye-left',
          {
            transform: 'translateY(0)',
          },
          {
            duration: 1,
            at: '<',
          },
        ],
        [
          '#eye-right',
          {
            transform: 'translateY(0)',
          },
          {
            duration: 1,
            at: '<',
          },
        ],
        [
          '#mouth',
          {
            transform: 'translateY(0) scaleY(1)',
          },
          {
            duration: 1,
            at: '<',
          },
        ]
      )
      mainTimeline = timeline(sequence, {
        repeat: Infinity,
      })
    },
  },
}
</script>

<style scoped>
#mouth,
#tear {
  transform-origin: center center;
  transform-box: fill-box;
}
</style>
