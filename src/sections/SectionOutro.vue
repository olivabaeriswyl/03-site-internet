<script setup>
import OutroAfterMovie from './../parts/OutroAfterMovie.vue'
import OutroMedia from './../parts/OutroMedia.vue'
import OutroInfo from './../parts/OutroInfo.vue'
</script>

<template>
  <div>
    <div id="burger-retour-image" class="burger-orange">
      <OutroAfterMovie></OutroAfterMovie>
    </div>

    <div id="burger-informations" class="burger-blue">
      <OutroMedia></OutroMedia>

      <OutroInfo></OutroInfo>
    </div>
  </div>
</template>

<style scoped></style>
