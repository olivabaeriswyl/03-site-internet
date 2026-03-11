<script setup>
import { ref, watch, onMounted } from 'vue'
// import gsap from 'gsap'
const heroImg = ref(null)
const view = ref(1)
onMounted(() => {
  watch(
    view,
    (newVal) => {
      console.log('view changed:', newVal)
      if (window.innerWidth > 600) {
        if (view.value === 1) {
          heroImg.value.style.transformOrigin = '10% 45%'
        } else if (view.value === 2) {
          heroImg.value.style.transformOrigin = '72% 58%'
        } else if (view.value === 3) {
          heroImg.value.style.transformOrigin = '54% 88%'
        } else if (view.value === 0) {
          heroImg.value.style.transformOrigin = 'center center'
          heroImg.value.style.scale = '50%'
        }
      } else {
        if (view.value === 1) {
          heroImg.value.style.transformOrigin = '2% 48.5%'
        } else if (view.value === 2) {
          heroImg.value.style.transformOrigin = '72% 58.5%'
        } else if (view.value === 3) {
          heroImg.value.style.transformOrigin = '46% 89%'
        } else if (view.value === 0) {
          heroImg.value.style.transformOrigin = 'center center'
          heroImg.value.style.scale = '50%'
        }
      }
    },
    { immediate: true },
  )
})
</script>

<template>
  <div class="heroContainer">
    <img ref="heroImg" src="/sapin.svg" alt="" />
  </div>
  <div class="scroll"></div>
  <div class="dev-nav">
    <div :class="{ active: view === 1 }" @click="view = 1"></div>
    <div :class="{ active: view === 2 }" @click="view = 2"></div>
    <div :class="{ active: view === 3 }" @click="view = 3"></div>
  </div>
</template>

<style scoped>
:global(html),
:global(body) {
  overflow: hidden;
}

.dev-nav {
  position: fixed;
  left: 0;
  top: 0;
  display: flex;
  flex-direction: column;
  gap: 10px;
  padding: 20px;
}

.dev-nav div {
  width: 20px;
  height: 20px;
  background: rgb(235, 197, 197);
  border-radius: 50%;
  cursor: pointer;
}

.dev-nav div.active {
  background: rgb(180, 100, 100);
}

.heroContainer {
  position: fixed;
  width: 100%;
  height: 100%;
  align-items: center;
  justify-content: center;
  display: flex;
}

img {
  width: 1000px;
  scale: 450%;
  height: auto;
  transition: all 3s ease;
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
