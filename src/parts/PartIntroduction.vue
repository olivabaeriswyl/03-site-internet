<script setup>
import { ref } from 'vue'
import gsap from 'gsap'
import { CustomEase } from 'gsap/CustomEase'

const heroImg = ref(null)
const h1 = ref(null)
const a = ref(null)
let moved = false
const tl = gsap.timeline()

const onCtaClick = () => {
  if (moved === false) {
    moved = !moved
    gsap.to(heroImg.value, {
      xPercent: -31,
      duration: 2,
      ease: CustomEase.create(
        'custom',
        'M0,0 C0.307,0.062 0.484,0.106 0.568,0.36 0.688,0.726 0.818,1.001 1,1 ',
      ),
    })
    tl.to(h1.value, { opacity: 0, duration: 1 }).to(a.value, { opacity: 0, duration: 1 })
    setTimeout(() => {
      // tl.clear()
      a.value.style.pointerEvents = 'none'
    }, 100)
  }
}
</script>

<template>
  <h1 ref="h1">Sapin porte-paroles</h1>
  <a ref="a" href="#" @click="onCtaClick">Débuter l’expérience</a>
  <img ref="heroImg" src="/background-test-nocrop.svg" alt="" />
  <div class="scroll"></div>
</template>

<style scoped>
:global(html),
:global(body) {
  overflow: hidden;
}

img {
  left: 0;
  top: 50%;
  transform: translate(-0.5%, -50%);
  height: 95vw;
  position: fixed;
  pointer-events: none;
}

.scroll {
  height: 300vh;
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
