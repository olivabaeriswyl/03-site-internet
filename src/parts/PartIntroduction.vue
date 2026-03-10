<script setup>
import { ref } from 'vue'
import gsap from 'gsap'
import { CustomEase } from 'gsap/CustomEase'

const heroImg = ref(null)
let moved = false

const onCtaClick = () => {
  // moved = !moved
  gsap.to(heroImg.value, {
    xPercent: moved ? -31 : 0,
    duration: 2,
    ease: CustomEase.create(
      'custom',
      'M0,0 C0.307,0.062 0.484,0.106 0.568,0.36 0.688,0.726 0.818,1.001 1,1 ',
    ),
  })
}
</script>

<template>
  <h1>Sapin porte-paroles</h1>
  <a href="#" @click="onCtaClick">Débuter l’expérience</a>
  <img ref="heroImg" src="/background-test-nocrop.svg" alt="" />
</template>

<style scoped>
img {
  left: 0;
  top: 50%;
  transform: translate(-0.5%, -50%);
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
