<script setup>
import { ref } from 'vue'
import gsap from 'gsap'
</script>

<template>
  <!-- <img ref="heroImg" src="/sapin.svg" alt="" /> -->
  <div class="container">
    <img class="t1" src="/tile-1.svg" alt="" />
    <img class="t2" src="/tile-2.svg" alt="" />
    <img class="t3" src="/tile-3.svg" alt="" />
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

.container {
  position: inherit;
}

@keyframes t1 {
  0% {
    transform: translate(0, 0);
  }
  100% {
    transform: translate(-100%, 0);
  }
}

@keyframes t2 {
  0% {
    transform: translate(100%, 0);
  }
  100% {
    transform: translate(0, 0);
  }
}

.t1 {
  object-fit: cover;
  object-position: center;
  position: absolute;
  inset: 0;
  width: 100%;
  height: 100%;
  aspect-ratio: 16 / 9; /* ou ton ratio */
  /* animation: t1 1s ease-out forwards; */
}

.t2 {
  transform: translate(100%, 0);
  object-fit: cover;
  object-position: center;
  position: absolute;
  inset: 0;
  width: 100%;
  height: 100%;
  aspect-ratio: 16 / 9; /* ou ton ratio */
  /* animation: t2 1s ease-out forwards; */
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
