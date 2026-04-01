<script setup>
defineProps({
  date: { type: String, required: true },
  location: { type: String, required: true },
  age: { type: String, required: true },
})
</script>

<template>
  <div class="timeline-text-item">
    <div class="timeline-text-wrapper">
      <div class="timeline-text-layout-line">
        <p class="timeline-text-date">{{ date }}</p>
        <div class="timeline-text-big-line"></div>
      </div>

      <p class="timeline-text-location">{{ location }}</p>

      <div class="timeline-text-layout-line-age">
        <p class="timeline-text-age">
          <strong>{{ age }}</strong>
        </p>
        <div class="timeline-text-age-line"></div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.timeline-text-wrapper {
  width: 210px;
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

.timeline-text-age {
  width: 190px;
}

/* Mise en page ligne */
.timeline-text-layout-line {
  display: flex;
  align-items: center;
}

.timeline-text-big-line {
  flex: 1;
  height: 1px;
  min-height: 1px;
  background-color: var(--color-orange);
  margin-left: 8px;
}

.timeline-text-layout-line-age {
  margin-top: 4px;

  display: flex;
  align-items: flex-start;
}

/* Animation apparition */
/* État initial */

.timeline-text-age-line {
  width: 26px;
  height: 1px;
  min-height: 1px;
  background-color: var(--color-orange);
  margin-left: 4px;
  margin-top: 9px;
  transform-origin: left;

  opacity: 1;
}

.timeline-text-age {
  transform: scale(0.9);
}

.timeline-text-date,
.timeline-text-location {
  opacity: 0;
  transform: translateY(5px);
}

.timeline-text-big-line {
  transform-origin: left;
  opacity: 0;
}

.timeline-text-layout-line-age {
  transform: translateY(-38px);
  will-change: transform;
}
</style>
