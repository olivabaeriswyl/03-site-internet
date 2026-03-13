<script setup>
import ButtonScroll from './../components/ButtonScroll.vue'
</script>

<template>
  <div class="screen">
    <div class="row">
      <div class="col-12">
        <div id="layout-button-scroll">
          <div id="position-button-scroll">
            <ButtonScroll></ButtonScroll>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.screen {
  height: 100vh;
  position: relative;
}

/* Position bouton scroll */

#position-button-scroll {
  position: absolute;
  left: 50%;
  transform: translateX(-50%);
  bottom: 0;
}
</style>
