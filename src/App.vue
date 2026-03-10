<script setup>
import PartOutro from './sections/SectionOutro.vue'
import PartIntro from './sections/SectionIntro.vue'
import PartStats from './sections/SectionStats.vue'
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

<style scoped></style>
