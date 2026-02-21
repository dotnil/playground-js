<template>
  <div class='progress-bar'>
    <div class='progress-bar__circle'>
      <svg viewBox="0 0 120 120" class="progress-bar__svg">
        <circle
          class="progress-bar__background"
          cx="60"
          cy="60"
          r="50"
        />

        <circle
          class="progress-bar__fill"
          cx="60"
          cy="60"
          r="50"
          :stroke-dasharray="circumference"
          :stroke-dashoffset="dashOffset"
        />
      </svg>

      <div class="progress-bar__text">
        {{ progress }}%
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue'

const progress = ref(0)

const radius = 50
const circumference = 2 * Math.PI * radius

const dashOffset = computed(() => {
  return circumference - (progress.value / 100) * circumference
})
</script>

<style>
.progress-bar {
  display: flex;
  justify-content: center;
  align-items: center;
  min-height: 100vh;
  margin: 0;
}

.progress-bar__circle {
  position: relative;
  width: 120px;
  height: 120px;
}

.progress-bar__svg {
  width: 100%;
  height: 100%;
  transform: rotate(-90deg);
}

.progress-bar__background {
  fill: transparent;
  stroke: #F2BDE0;
  stroke-width: 10;
}

.progress-bar__fill {
  fill: transparent;
  stroke: #FF69B4;
  stroke-width: 10;
  stroke-linecap: round;
  transition: stroke-dashoffset 0.3s ease;
}

.progress-bar__text {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  font-size: 20px;
  font-weight: bold;
  font-family: sans-serif;
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100px;
  height: 100px;
}
</style>
