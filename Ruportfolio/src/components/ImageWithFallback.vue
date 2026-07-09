<script setup>
import { ref } from 'vue'

defineProps({
  src: {
    type: String,
    default: '',
  },
  alt: {
    type: String,
    default: '',
  },
})

const failed = ref(false)
</script>

<template>
  <img v-if="src && !failed" :src="src" :alt="alt" @error="failed = true" />
  <div v-else class="image-fallback" role="img" :aria-label="alt">
    <span>NM</span>
  </div>
</template>

<style scoped>
img,
.image-fallback {
  display: block;
}

.image-fallback {
  display: flex;
  align-items: center;
  justify-content: center;
  color: rgba(240, 242, 248, 0.78);
  background:
    linear-gradient(135deg, rgba(155, 35, 53, 0.35), rgba(10, 15, 26, 0.95)),
    var(--color-panel);
  font-family: var(--font-display);
  font-size: clamp(3rem, 8vw, 5rem);
  font-weight: 800;
}
</style>
