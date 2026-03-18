<script setup>
import { ref } from 'vue'

const copied = ref(false)

const copyLink = async () => {
  try {
    const url = window.location.origin + window.location.pathname

    await navigator.clipboard.writeText(url)

    copied.value = true

    setTimeout(() => {
      copied.value = false
    }, 1000)
  } catch (e) {
    console.error('Erreur copie', e)
  }
}
</script>

<template>
  <button @click="copyLink" :class="['btn-share', { 'btn-share--copied': copied }]">
    <strong>{{ copied ? 'Lien copié' : 'Partager le site' }}</strong>
  </button>
</template>

<style scoped>
.btn-share {
  border-radius: 29px;
  padding: 12px 32px 15px;
  width: 100%;
  margin-top: 24px;

  border: 1.4px solid #8fa9c8;
  background-color: var(--color-light-blue);
  color: var(--color-blue);

  transition:
    transform 0.4s ease,
    color 0.2s ease,
    border 0.2s ease;
}

button:hover {
  color: var(--color-orange);
  border: 1.4px solid var(--color-orange);
  transform: scale(1.04);
}

.btn-share--copied {
  color: var(--color-orange);
  border: 1.4px solid var(--color-orange);
  transform: scale(1.04);
}
</style>
