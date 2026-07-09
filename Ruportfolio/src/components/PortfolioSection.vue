<script setup>
import ImageWithFallback from './ImageWithFallback.vue'
import SectionHeading from './SectionHeading.vue'
import { portfolioItems } from '../data/portfolioData'
</script>

<template>
  <section id="portfolio" class="section section--dark">
    <div class="container">
      <SectionHeading title="Portfolio" />

      <div class="portfolio-grid">
        <article v-for="item in portfolioItems" :key="item.title" class="portfolio-card">
          <ImageWithFallback :src="item.image" :alt="item.title" class="portfolio-card__image" />
          <div class="portfolio-card__overlay">
            <div>
              <p>{{ item.category }} · {{ item.year }}</p>
              <h3>{{ item.title }}</h3>
            </div>
            <span aria-hidden="true">↗</span>
          </div>
        </article>
      </div>
    </div>
  </section>
</template>

<style scoped>
.portfolio-grid {
  display: grid;
  grid-template-columns: repeat(3, minmax(0, 1fr));
  gap: 24px;
  margin-top: 56px;
}

.portfolio-card {
  position: relative;
  overflow: hidden;
  aspect-ratio: 4 / 3;
  border-radius: 2px;
  background: var(--color-panel);
  cursor: pointer;
  transition: transform 220ms ease;
}

.portfolio-card:hover {
  transform: scale(1.02);
}

.portfolio-card__image {
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: transform 420ms ease;
}

.portfolio-card:hover .portfolio-card__image {
  transform: scale(1.08);
}

.portfolio-card__overlay {
  position: absolute;
  inset: 0;
  display: flex;
  align-items: flex-end;
  justify-content: space-between;
  gap: 16px;
  padding: 24px;
  color: #fff;
  background: linear-gradient(to top, rgba(155, 35, 53, 0.92), transparent);
  opacity: 0;
  transition: opacity 220ms ease;
}

.portfolio-card:hover .portfolio-card__overlay {
  opacity: 1;
}

p {
  margin: 0 0 6px;
  color: rgba(255, 255, 255, 0.72);
  font-size: 0.74rem;
  letter-spacing: 0.14em;
  text-transform: uppercase;
}

h3 {
  margin: 0;
  color: #fff;
  font-family: var(--font-display);
  font-size: 1.1rem;
}

.portfolio-card__overlay span {
  font-size: 1.25rem;
}

@media (max-width: 980px) {
  .portfolio-grid {
    grid-template-columns: repeat(2, minmax(0, 1fr));
  }
}

@media (max-width: 620px) {
  .portfolio-grid {
    grid-template-columns: 1fr;
  }
}
</style>
