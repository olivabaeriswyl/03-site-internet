<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

const heroImg = ref(null)

// Scroll virtuel
let targetScroll = 0
let currentScroll = 0
let rafId = 0

const MIN = 0
const MAX = 4000 // "longueur" du fake scroll
const SMOOTH = 0.08 // lissage
const SPEED = 1 // sensibilité molette
const PARALLAX = 0.35 // facteur de déplacement X

const clamp = (v, min, max) => Math.max(min, Math.min(max, v))

const onWheel = (e) => {
  e.preventDefault()
  targetScroll = clamp(targetScroll + e.deltaY * SPEED, MIN, MAX)
}

const tick = () => {
  currentScroll += (targetScroll - currentScroll) * SMOOTH
  const x = -currentScroll * PARALLAX

  if (heroImg.value) {
    heroImg.value.style.setProperty('--bg-x', `${x}px`)
  }

  rafId = requestAnimationFrame(tick)
}

const onCtaClick = (e) => {
  e.preventDefault()
  targetScroll = clamp(targetScroll + 600, MIN, MAX)
}

onMounted(() => {
  window.addEventListener('wheel', onWheel, { passive: false })
  rafId = requestAnimationFrame(tick)
})

onUnmounted(() => {
  window.removeEventListener('wheel', onWheel)
  cancelAnimationFrame(rafId)
})
</script>

<template>
  <h1>Sapin porte-paroles</h1>
  <a href="#" @click="onCtaClick">Débuter l’expérience</a>
  <img ref="heroImg" src="/background-test-nocrop.svg" alt="" />
</template>

<style scoped>
:global(html),
:global(body) {
  overflow: hidden; /* important pour le fake scroll */
}

img {
  left: 0;
  top: 50%;
  transform: translate(calc(-0.5% + var(--bg-x, 0px)), -50%);
  height: 95vw;
  position: fixed;
  pointer-events: none;
}

a {
  position: absolute;
  left: 50%;
  bottom: 20%;
  transform: translate(-50%, 0);
  width: 170px;
  height: 170px;
  display: flex;
  flex-flow: row nowrap;
  justify-content: center;
  align-items: center;
  border: 1px solid orange;
  border-radius: 50%;
  color: orange;
}
</style>
