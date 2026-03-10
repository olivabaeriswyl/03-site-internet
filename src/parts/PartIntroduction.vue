<script setup></script>

<template>
  <h1>Sapin porte-paroles</h1>
  <a href="#">Débuter l’expérience</a>
  <img src="/background-test-nocrop.svg" alt="" />
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
