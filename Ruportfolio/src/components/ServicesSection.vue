<script setup>
import SectionHeading from './SectionHeading.vue'
import { services } from '../data/portfolioData'
</script>

<template>
  <section id="services" class="section section--base">
    <div class="container">
      <SectionHeading title="Services" />

      <div class="services-grid">
        <article v-for="service in services" :key="service.title" class="service-card">
          <div class="service-card__icon" aria-hidden="true">{{ service.icon }}</div>
          <h3>{{ service.title }}</h3>
          <p>{{ service.desc }}</p>
        </article>
      </div>
    </div>
  </section>
</template>

<style scoped>
.services-grid {
  display: grid;
  grid-template-columns: repeat(3, minmax(0, 1fr));
  gap: 24px;
  margin-top: 56px;
}

.service-card {
  min-height: 240px;
  padding: 32px;
  border: 1px solid rgba(155, 35, 53, 0.15);
  border-radius: 2px;
  background: var(--color-panel);
  transition:
    border-color 180ms ease,
    transform 180ms ease;
}

.service-card:hover {
  border-color: rgba(155, 35, 53, 0.5);
  transform: translateY(-4px);
}

.service-card__icon {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 56px;
  height: 56px;
  margin-bottom: 24px;
  border: 1px solid rgba(155, 35, 53, 0.25);
  border-radius: 2px;
  color: var(--color-accent);
  background: rgba(155, 35, 53, 0.1);
  font-size: 1.25rem;
}

h3 {
  margin: 0 0 12px;
  color: var(--color-text);
  font-family: var(--font-display);
  font-size: 1.12rem;
}

p {
  margin: 0;
  color: var(--color-muted);
  font-size: 0.9rem;
  line-height: 1.7;
}

@media (max-width: 980px) {
  .services-grid {
    grid-template-columns: repeat(2, minmax(0, 1fr));
  }
}

@media (max-width: 620px) {
  .services-grid {
    grid-template-columns: 1fr;
  }
}
</style>
