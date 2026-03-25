<script setup>
defineProps({
  date: { type: String, required: true },
  location: { type: String, required: true },
  age: { type: String, required: true },
})
</script>

<template>
  <div class="timeline-item">
    <div id="timeline-wrapper">
      <div id="big-line"></div>
      <div id="layout-text">
        <p>{{ date }}</p>
        <p>{{ location }}</p>
        <p id="strong-text">
          <strong>{{ age }}</strong>
        </p>
      </div>
    </div>
  </div>
</template>

<style scoped>
#timeline-wrapper {
  width: 210px;
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

#strong-text {
  margin-top: 4px;
}

/* Mise en page ligne */
#big-line {
  height: 65px;
  width: 1px;
  background-color: var(--color-orange);
  margin-right: 6px;
}
</style>
