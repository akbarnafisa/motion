<template>
  <button class="button-play">
    <svg xmlns="http://www.w3.org/2000/svg" width="18" height="18">
      <path
        d="M 7.063 0.288 C 7.257 -0.096 7.743 -0.096 7.937 0.288 L 14.932 14.135 C 15.126 14.519 14.883 15 14.495 15 L 0.505 15 C 0.117 15 -0.126 14.519 0.068 14.135 Z"
        transform="translate(1.5 1.642) rotate(90 7.5 7.5)"
        fill="white"
        stroke-width="2"
        stroke="rgb(255, 255, 255)"
        stroke-linecap="round"
        stroke-linejoin="round"
      ></path>
    </svg>
  </button>
</template>

<style scoped>
.button-play {
  outline: none;
  background: rgb(87, 235, 100);
  border: none;
  width: 40px;
  height: 40px;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  box-shadow: rgba(87, 235, 100, 0.333) 2px 2px 0px 0px;
  cursor: pointer;
  position: absolute;
  bottom: 24px;
  right: 24px;
}
</style>
