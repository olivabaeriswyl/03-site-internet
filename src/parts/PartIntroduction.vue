<script setup>
import { ref, onMounted, onUnmounted } from 'vue'
import { gsap } from 'gsap'
import { ScrollTrigger } from 'gsap/ScrollTrigger'
gsap.registerPlugin(ScrollTrigger)

const heroImg = ref(null)
const heroContainer = ref(null)

onMounted(() => {
  if (heroImg?.value && heroContainer?.value) {
    console.log('ok')
    gsap.to(heroImg.value, {
      // transformOrigin: '10% 45%',
      // x: '-200%',
      // y: '-100%',
      // duration: 10,

      scrollTrigger: {
        trigger: heroContainer.value,
        start: 'top top',
        // end: 'bottom top',
        scrub: true,
      },
    })
  }
})
// const view = ref(1)
// const origins = {
//   desktop: [
//     { x: 10, y: 45 },
//     { x: 72, y: 58 },
//     { x: 54, y: 88 },
//     { x: 50, y: 50 },
//   ],
//   mobile: [
//     { x: 2, y: 48.5 },
//     { x: 72, y: 58.5 },
//     { x: 46, y: 89 },
//     { x: 50, y: 50 },
//   ],
// }

// onMounted(() => {
//   heroImg.value.style.transformOrigin = '10% 45%'
//   window.addEventListener('wheel', onWheel, { passive: false })
//   rafId = requestAnimationFrame(tick)
// })

// onUnmounted(() => {
//   window.removeEventListener('wheel', onWheel)
//   cancelAnimationFrame(rafId)
// })
</script>

<template>
  <div ref="heroContainer" class="heroContainer">
    <img ref="heroImg" class="heroImg" src="/sapin.svg" alt="" />
  </div>
  <div class="scroll"></div>
</template>

<style scoped>
:global(html),
:global(body) {
  padding: 0;
  margin: 0;
}

/* .heroContainer {
  width: 100vw;
  height: 100vh;
  overflow: hidden;
  position: relative;
  background-color: aqua;
}

.heroImg {
  position: absolute;
  top: 0%;
  left: 0%;
  width: 1000px;
  scale: 500%;
  height: auto;
} */

/* :global(html),
:global(body) {
  overflow: hidden;
}*/

/* .scroll {
  height: 200vh;
} */

.heroContainer {
  position: relative;
  overflow: hidden;
  width: 100vw;
  height: 300vh;
  align-items: center;
  justify-content: center;
  display: flex;
}

img {
  width: 80vw;
  scale: 450%;
  position: absolute;
  top: 0;
  left: 0;
  /* transition: all 3s ease; */
}

@media (min-width: 600px) {
  img {
    scale: 500%;
  }
}

@media (min-width: 1400px) {
  img {
    width: 80vw;
  }
}

/* @media (max-aspect-ratio: 16/10) {
  img {
    width: auto;
    position: fixed;
    left: 0;
    top: 0;
  }
} */
</style>
