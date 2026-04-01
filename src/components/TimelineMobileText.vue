<script setup>
defineProps({
  date: { type: String, required: true },
  location: { type: String, required: true },
  age: { type: String, required: true },
})
</script>

<template>
  <div class="timeline-mobile-text-item">
    <div id="timeline-mobile-text-wrapper">
      <div id="timeline-mobile-big-line"></div>
      <div id="timeline-mobile-text-layout">
        <p>{{ date }}</p>
        <p>{{ location }}</p>
        <p id="timeline-mobile-strong-text">
          <strong>{{ age }}</strong>
        </p>
      </div>
    </div>
  </div>
</template>

<style scoped>
#timeline-mobile-text-wrapper {
  width: 200px;
  display: flex;
}

p {
  color: var(--color-orange);
  font-family: arima, sans-serif;
  font-size: 16px;
  font-weight: 400;
  line-height: 16px;
  margin: 0;
}

strong {
  font-size: 15px;
  font-weight: 700;
  line-height: 16px;
}

#timeline-mobile-strong-text {
  margin-top: 4px;
}

/* Mise en page ligne */
#timeline-mobile-big-line {
  height: 75px;
  width: 1px;
  min-width: 1px;
  background-color: var(--color-orange);
  margin-right: 6px;
}

/* Animation apparition texte */
.timeline-mobile-text-item {
  transform-origin: top left;
  will-change: transform;
}
</style>
