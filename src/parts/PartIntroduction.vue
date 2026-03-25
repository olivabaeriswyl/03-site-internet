<script setup>
import { ref, onMounted } from 'vue'
import { gsap } from 'gsap'
import { ScrollTrigger } from 'gsap/ScrollTrigger'
gsap.registerPlugin(ScrollTrigger)

const heroImg = ref(null)
const heroContainer = ref(null)

onMounted(() => {
  const isMobile = window.innerWidth < 800

  const values = isMobile
    ? {
        startX: '135%',
        startY: '-15%',
        midX: '-120%',
        midY: '-50%',
        endX: '65%',
        endY: '-250%',
      }
    : {
        startX: '175%',
        startY: '-10%',
        midX: '-90%',
        midY: '-60%',
        endX: '80%',
        endY: '-270%',
      }
  ctx = gsap.context(() => {
    gsap.set(heroImg.value, {
      x: values.startX,
      y: values.startY,
    })

    const tl = gsap.timeline({
      scrollTrigger: {
        trigger: heroContainer.value,
        start: 'top top',
        end: 'bottom top',
        scrub: true,
      },
    })

    // 1ère moitié du scroll → point A
    tl.to(heroImg.value, {
      x: values.midX,
      y: values.midY,
    })

    // 2ème moitié du scroll → point B
    tl.to(heroImg.value, {
      x: values.endX,
      y: values.endY,
    })
  })
})
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
  width: 1200px;
  scale: 450%;
  position: fixed;
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
</style>
