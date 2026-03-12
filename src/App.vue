<script setup>
import PartOutro from './sections/SectionOutro.vue'
import PartIntro from './sections/SectionIntro.vue'
import PartStats from './sections/SectionStats.vue'
import BurgerMenu from './components/BurgerMenu.vue'

import { onMounted, ref } from 'vue'
import { gsap } from 'gsap'
</script>

<template>
  <header>
    <PartIntro></PartIntro>
  </header>
  <main>
    <PartStats></PartStats>
  </main>
  <footer>
    <PartOutro></PartOutro>
  </footer>
</template>

<style scoped>
header {
  padding-top: 100px;
  background-color: var(--color-light-orange);
  color: var(--color-white);
}

@media (max-width: 992px) {
  header {
    padding-top: 50px;
  }
}

@media (max-width: 768px) {
  header {
    padding-top: 40px;
  }
}

@media (max-width: 576px) {
  header {
    padding-top: 10px;
  }
}
</style>
