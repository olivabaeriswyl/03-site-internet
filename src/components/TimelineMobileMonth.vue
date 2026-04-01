<script setup>
defineProps({
  month: { type: String, required: true },
})
</script>

<template>
  <div>
    <div>
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
  padding-bottom: 4px;
}
</style>
