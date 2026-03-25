<script setup>
import { ref, onMounted } from 'vue'
import { gsap } from 'gsap'
import { ScrollTrigger } from 'gsap/ScrollTrigger'
gsap.registerPlugin(ScrollTrigger)

const heroImg = ref(null)
const heroContainer = ref(null)

onMounted(() => {
  ctx = gsap.context(() => {
    gsap.set(heroImg.value, {
      x: '175%',
      y: '-10%',
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
      x: '-90%',
      y: '-60%',
    })

    // 2ème moitié du scroll → point B
    tl.to(heroImg.value, {
      x: '80%',
      y: '-270%',
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
