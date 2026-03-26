<script setup>
import { ref, onMounted, onUnmounted } from 'vue'
import { gsap } from 'gsap'
import { ScrollTrigger } from 'gsap/ScrollTrigger'
gsap.registerPlugin(ScrollTrigger)

const heroImg = ref(null)
const heroContainer = ref(null)
let ctx

onMounted(() => {
  const isMobile = window.innerWidth < 600

  const values = isMobile
    ? {
        startX: '0',
        midX: '0',
        endX: '0',
      }
    : {
        startX: '0',
        midX: '-20%',
        endX: '0',
      }
  ctx = gsap.context(() => {
    gsap.set(heroImg.value, {
      x: values.startX,
      y: values.startY,
    })
  })
})

onUnmounted(() => ctx.revert())
</script>

<template>
  <div class="bg-container">
    <img class="bg-img" src="/bg-p1.svg" alt="" />
    <img class="bg-img-2" src="/bg-p2.svg" alt="" />
    <img class="bg-img-3" src="/bg-p3.svg" alt="" />
  </div>
  <div class="mobile-bg-container">
    <img class="mobile-bg" src="/intro-mobile-bg.svg" alt="" />
  </div>
</template>

<style scoped>
.bg-container {
  display: none;
  position: sticky;
  overflow: hidden;
  inset: 0;
  z-index: 2;
  height: 100vh;
  display: flex;
  flex-flow: row nowrap;
  align-items: center;
  pointer-events: none;
}

.mobile-bg-container {
  position: absolute;
  top: 0;
  left: 0;
  /* overflow: hidden; */
  z-index: 1;
  width: 100%;
  height: 400vh;
}

.mobile-bg {
  height: 100%;
  left: 50%;
  transform: translateX(-50%);
  width: auto;
  position: absolute;
}

.bg-img,
.bg-img-2,
.bg-img-3 {
  position: absolute;
  left: 50%;
  min-width: 100vw;
  display: none;
}

.bg-img {
  transform: translate(-50%, 0);
}

.bg-img-2 {
  transform: translate(50%, 0);
}

.bg-img-3 {
  transform: translate(150%, 0);
}

@media (max-aspect-ratio: 19/9) {
  .bg-img,
  .bg-img-2,
  .bg-img-3 {
    height: 100vh;
    min-width: none;
  }
}

@media (min-width: 600px) {
  .mobile-bg-container,
  .mobile-bg {
    display: none;
  }

  .bg-container {
    display: block;
  }

  .bg-img,
  .bg-img-2,
  .bg-img-3 {
    display: block;
  }
}
</style>
