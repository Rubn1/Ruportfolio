<script setup>
import ImageWithFallback from './ImageWithFallback.vue'
import { socialLinks } from '../data/portfolioData'
import profileImage from '../assets/image1.jpeg'

defineEmits(['navigate'])
</script>

<template>
  <section id="home" class="hero">
    <div class="hero__stars" aria-hidden="true">
      <span v-for="item in 60" :key="item"></span>
    </div>

    <div class="container hero__grid">
      <div class="hero__content">
        <p class="hero__eyebrow">Hello, I'm</p>
        <h1>
          Ndabunguye
          <span>Mercy</span>
        </h1>
        <p class="hero__subtitle">Software Engineer &amp; Creative Designer</p>

        <div class="hero__actions">
          <button class="button" type="button" @click="$emit('navigate', 'Contact')">Hire Me</button>
          <button class="button button--ghost" type="button" @click="$emit('navigate', 'Portfolio')">
            My Work
          </button>
        </div>

        <div class="hero__socials" aria-label="Social links">
          <a v-for="link in socialLinks" :key="link.label" :href="link.href" :aria-label="link.label">
            {{ link.label.charAt(0) }}
          </a>
        </div>
      </div>

      <div class="hero__portrait">
        <div class="hero__portrait-frame">
          <span class="hero__ring hero__ring--one" aria-hidden="true"></span>
          <span class="hero__ring hero__ring--two" aria-hidden="true"></span>
          <ImageWithFallback :src="profileImage" alt="Professional portrait" class="hero__image" />
        </div>
      </div>
    </div>

    <div class="hero__scroll-cue" aria-hidden="true">
      <span>Scroll</span>
      <strong>⌄</strong>
    </div>
  </section>
</template>

<style scoped>
.hero {
  position: relative;
  display: flex;
  align-items: center;
  min-height: 100vh;
  overflow: hidden;
  background:
    radial-gradient(ellipse 80% 80% at 70% 50%, rgba(155, 35, 53, 0.08), transparent 60%),
    var(--color-bg);
}

.hero__stars {
  position: absolute;
  inset: 0;
  pointer-events: none;
}

.hero__stars span {
  position: absolute;
  width: 2px;
  height: 2px;
  border-radius: 50%;
  background: rgba(240, 242, 248, 0.3);
}

.hero__stars span:nth-child(3n) {
  left: 18%;
  top: 22%;
}

.hero__stars span:nth-child(3n + 1) {
  left: 72%;
  top: 36%;
}

.hero__stars span:nth-child(3n + 2) {
  left: 46%;
  top: 68%;
}

.hero__grid {
  position: relative;
  display: grid;
  grid-template-columns: minmax(0, 1fr) minmax(280px, 0.8fr);
  align-items: center;
  gap: 48px;
  padding-block: 112px 72px;
}

.hero__content {
  animation: slide-in-left 700ms ease both;
}

.hero__eyebrow {
  margin: 0 0 16px;
  color: var(--color-accent);
  font-size: 0.88rem;
  letter-spacing: 0.16em;
  text-transform: uppercase;
}

h1 {
  margin: 0 0 18px;
  color: var(--color-text);
  font-family: var(--font-display);
  font-size: clamp(2.8rem, 8vw, 5.5rem);
  font-weight: 800;
  line-height: 1.05;
}

h1 span {
  display: block;
  color: #fff;
}

.hero__subtitle {
  margin: 0 0 32px;
  color: var(--color-muted);
  font-size: 1.08rem;
}

.hero__actions,
.hero__socials {
  display: flex;
  align-items: center;
  flex-wrap: wrap;
  gap: 16px;
}

.hero__socials {
  gap: 20px;
  margin-top: 40px;
}

.hero__socials a {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  width: 36px;
  height: 36px;
  border: 1px solid rgba(155, 35, 53, 0.3);
  border-radius: 50%;
  color: var(--color-muted);
  font-size: 0.8rem;
  transition:
    border-color 180ms ease,
    color 180ms ease,
    background 180ms ease;
}

.hero__socials a:hover {
  border-color: var(--color-accent);
  color: var(--color-accent);
  background: rgba(155, 35, 53, 0.1);
}

.hero__portrait {
  display: flex;
  justify-content: flex-end;
  animation: slide-in-right 700ms 120ms ease both;
}

.hero__portrait-frame {
  position: relative;
}

.hero__ring {
  position: absolute;
  border: 1px solid var(--color-accent);
  border-radius: 50%;
  pointer-events: none;
}

.hero__ring--one {
  inset: -16px;
  opacity: 0.2;
}

.hero__ring--two {
  inset: -32px;
  opacity: 0.1;
}

.hero__image {
  position: relative;
  width: clamp(280px, 35vw, 420px);
  height: clamp(280px, 35vw, 420px);
  border-radius: 50%;
  object-fit: cover;
  object-position: top;
  box-shadow:
    0 0 60px rgba(155, 35, 53, 0.25),
    0 0 120px rgba(13, 18, 32, 0.8);
  filter: brightness(0.95) contrast(1.05);
}

.hero__scroll-cue {
  position: absolute;
  left: 50%;
  bottom: 32px;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 4px;
  color: var(--color-muted);
  opacity: 0.45;
  transform: translateX(-50%);
}

.hero__scroll-cue span {
  font-size: 0.74rem;
  letter-spacing: 0.16em;
  text-transform: uppercase;
}

.hero__scroll-cue strong {
  color: var(--color-accent);
  font-size: 1.25rem;
}

@keyframes slide-in-left {
  from {
    opacity: 0;
    transform: translateX(-40px);
  }
  to {
    opacity: 1;
    transform: translateX(0);
  }
}

@keyframes slide-in-right {
  from {
    opacity: 0;
    transform: translateX(40px);
  }
  to {
    opacity: 1;
    transform: translateX(0);
  }
}

@media (max-width: 820px) {
  .hero__grid {
    grid-template-columns: 1fr;
    padding-top: 104px;
  }

  .hero__portrait {
    justify-content: center;
  }
}
</style>
