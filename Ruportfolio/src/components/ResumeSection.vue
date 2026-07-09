<script setup>
import SectionHeading from './SectionHeading.vue'
import { experience, skills } from '../data/portfolioData'
</script>

<template>
  <section id="resume" class="section section--dark">
    <div class="container">
      <SectionHeading title="My Skills" />

      <div class="resume">
        <div class="resume__skills">
          <div v-for="skill in skills" :key="skill.name" class="skill">
            <div class="skill__header">
              <span>{{ skill.name }}</span>
              <strong>{{ skill.level }}%</strong>
            </div>
            <div class="skill__track">
              <span :style="{ width: `${skill.level}%` }"></span>
            </div>
          </div>
        </div>

        <div class="timeline">
          <article v-for="item in experience" :key="item.role" class="timeline__item">
            <p>{{ item.period }}</p>
            <h3>{{ item.role }}</h3>
            <strong>{{ item.company }}</strong>
            <span>{{ item.desc }}</span>
          </article>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.resume {
  display: grid;
  grid-template-columns: minmax(0, 1fr) minmax(0, 1fr);
  gap: 64px;
  margin-top: 56px;
}

.resume__skills {
  display: grid;
  align-content: start;
  gap: 24px;
}

.skill__header {
  display: flex;
  justify-content: space-between;
  gap: 16px;
  margin-bottom: 8px;
}

.skill__header span,
.skill__header strong {
  font-size: 0.9rem;
}

.skill__header span {
  color: var(--color-text);
}

.skill__header strong {
  color: var(--color-accent);
  font-weight: 500;
}

.skill__track {
  height: 4px;
  overflow: hidden;
  border-radius: 999px;
  background: rgba(155, 35, 53, 0.15);
}

.skill__track span {
  display: block;
  height: 100%;
  border-radius: inherit;
  background: var(--color-accent);
  animation: grow-bar 900ms ease both;
}

.timeline {
  display: grid;
  gap: 32px;
}

.timeline__item {
  position: relative;
  padding-left: 32px;
  border-left: 2px solid rgba(155, 35, 53, 0.3);
}

.timeline__item::before {
  position: absolute;
  top: 4px;
  left: -9px;
  width: 16px;
  height: 16px;
  border-radius: 50%;
  background: var(--color-accent);
  content: '';
}

.timeline__item p {
  margin: 0 0 6px;
  color: var(--color-accent);
  font-size: 0.74rem;
  letter-spacing: 0.14em;
  text-transform: uppercase;
}

.timeline__item h3 {
  margin: 0 0 6px;
  color: var(--color-text);
  font-size: 1rem;
}

.timeline__item strong {
  display: block;
  margin-bottom: 10px;
  color: rgba(155, 35, 53, 0.85);
  font-size: 0.88rem;
}

.timeline__item span {
  display: block;
  color: var(--color-muted);
  font-size: 0.9rem;
  line-height: 1.7;
}

@keyframes grow-bar {
  from {
    width: 0;
  }
}

@media (max-width: 820px) {
  .resume {
    grid-template-columns: 1fr;
  }
}
</style>
