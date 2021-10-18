<script setup>
// This starter template is using Vue 3 <script setup> SFCs
// Check out https://v3.vuejs.org/api/sfc-script-setup.html#sfc-script-setup
import Stagger from './components/Stagger.vue'
import Timeline from './components/Timeline.vue'
import Easing from './components/Easing.vue'
import HandDraw from './components/HandDraw.vue'
import PaymentSuccess from './components/PaymentSuccess.vue'
import PaymentPending from './components/PaymentPending.vue'
import PaymentFailed from './components/PaymentFailed.vue'
import lock from './components/lock.vue'
import NfcCard from './components/NfcCard.vue'
import ErrorGeneral from './components/ErrorGeneral.vue'
import ErrorNetwork from './components/ErrorNetwork.vue'
import Lose from './components/Lose.vue'
import Win from './components/Win.vue'
</script>

<template>
  <Stagger />
  <Easing />
  <Timeline />
  <!-- <HandDraw /> -->
  <PaymentSuccess />
  <PaymentFailed />
  <PaymentPending />
  <lock />
  <NfcCard />
  <ErrorGeneral />
  <ErrorNetwork />
  <Lose />
  <Win />
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.main-container {
  border: 1px solid rgba(0, 0, 0, 0.2);
  border-radius: 8px;
  padding: 24px;
  height: 400px;
  width: 100%;
  max-width: 500px;
  margin: 0 auto 24px auto;
  display: flex;
  align-items: center;
  justify-content: center;
  position: relative;
}
</style>
