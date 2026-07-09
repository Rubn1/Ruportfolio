<script setup>
defineProps({
  title: {
    type: String,
    required: true,
  },
})
</script>

<template>
  <div class="section-heading">
    <h2>{{ title }}</h2>
    <span aria-hidden="true"></span>
  </div>
</template>

<style scoped>
.section-heading {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 12px;
}

h2 {
  margin: 0;
  color: var(--color-accent);
  font-size: 0.88rem;
  font-weight: 600;
  letter-spacing: 0.16em;
  text-transform: uppercase;
}

span {
  width: 48px;
  height: 1px;
  background: var(--color-accent);
}
</style>
