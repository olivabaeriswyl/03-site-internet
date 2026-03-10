<script setup>
import IntroStart from './../parts/IntroStart.vue'
import IntroWords from './../parts/IntroWords.vue'
import IntroText from './../parts/IntroText.vue'
</script>

<template>
  <div>
    <IntroStart></IntroStart>

    <IntroWords></IntroWords>

    <IntroText></IntroText>
  </div>
</template>

<style scoped>
div {
  background-color: var(--color-light-orange);
  color: var(--color-white);
}
</style>
