<script setup>
defineProps({
  month: { type: String, required: true },
})
</script>

<template>
  <div class="timeline-item month-position">
    <div id="timeline-wrapper">
      <p>{{ month }}</p>
    </div>
  </div>
</template>

<style scoped>
p {
  color: var(--color-orange);
  font-family: arima, sans-serif;
  font-size: 16px;
  font-weight: 400;
  line-height: 16px;
  margin: 0;
  padding-top: 3px;
}
</style>
