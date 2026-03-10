<script setup>
import { ref, onMounted } from 'vue'
import gsap from 'gsap'

const t2 = ref(null)
const t3 = ref(null)

onMounted(() => {
  t2.value.addEventListener('load', () => {
    const t2Width = t2.value.getBoundingClientRect().width
    t3.value.style.transform = `translate(calc(100vw + ${t2Width}px), 0)`
    console.log('t2 width:', t2Width)
  })
})
</script>

<template>
  <!-- <img ref="heroImg" src="/sapin.svg" alt="" /> -->
  <div class="container">
    <img class="t1" src="/tile-1.svg" alt="" />
    <img ref="t2" class="t2" src="/tile-2.svg" alt="" />
    <img ref="t3" class="t3" src="/tile-3.svg" alt="" />
    <img class="t4" src="/tile-4.svg" alt="" />
    <img class="t5" src="/tile-5.svg" alt="" />
    <img class="t6" src="/tile-6.svg" alt="" />
  </div>
  <div class="scroll"></div>
</template>

<style scoped>
:global(html),
:global(body) {
  overflow: hidden;
}

/* img {
  position: fixed;
  transform: translate(-4%, -41%);
  left: 0;
  width: 360vw;
} */

@keyframes slide {
  0% {
    transform: translateX(0);
  }
  100% {
    transform: translateX(-200vw);
  }
}

.container {
  position: fixed;
  inset: 0;
  width: 100%;
  height: 100%;
  pointer-events: none;
  animation: slide 6s linear infinite;
}

.t1 {
  transform: translate(0%, 0);
  object-fit: cover;
  object-position: right;
  position: absolute;
  inset: 0;
  width: 100%;
  height: 100%;
  aspect-ratio: 16 / 9; /* ou ton ratio */
}

.t2 {
  object-position: center;
  position: absolute;
  inset: 0;
  left: 100vw;
  width: auto;
  height: 100%;
}

.t3 {
  object-fit: cover;
  object-position: left;
  position: absolute;
  inset: 0;
  width: 100%;
  height: 100%;
  aspect-ratio: 16 / 9; /* ou ton ratio */
}

@media (min-aspect-ratio: 14.8/7.8) {
  .t2 {
    transform: translate(100%, 0);
    object-fit: cover;
    object-position: center;
    position: absolute;
    inset: 0;
    width: 100%;
    height: 100%;
    aspect-ratio: 16 / 9; /* ou ton ratio */
  }

  .t3 {
    transform: translate(200%, 0);
    object-fit: cover;
    object-position: center;
    position: absolute;
    inset: 0;
    width: 100%;
    height: 100%;
    aspect-ratio: 16 / 9; /* ou ton ratio */
  }
}
.t4 {
  transform: translate(0, -100%);
  object-fit: cover;
  object-position: center;
  position: absolute;
  inset: 0;
  width: 100%;
  height: 100%;
  aspect-ratio: 16 / 9; /* ou ton ratio */
}
.t5 {
  transform: translate(100%, -100%);
  object-fit: cover;
  object-position: center;
  position: absolute;
  inset: 0;
  width: 100%;
  height: 100%;
  aspect-ratio: 16 / 9; /* ou ton ratio */
}
.t6 {
  transform: translate(200%, -100%);
  object-fit: cover;
  object-position: center;
  position: absolute;
  inset: 0;
  width: 100%;
  height: 100%;
  aspect-ratio: 16 / 9; /* ou ton ratio */
}
</style>
