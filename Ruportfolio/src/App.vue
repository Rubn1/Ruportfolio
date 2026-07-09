<script setup>
import { onMounted, onUnmounted, ref } from 'vue'
import AppFooter from './components/AppFooter.vue'
import AppHeader from './components/AppHeader.vue'
import AboutSection from './components/AboutSection.vue'
import ContactSection from './components/ContactSection.vue'
import HeroSection from './components/HeroSection.vue'
import PortfolioSection from './components/PortfolioSection.vue'
import ResumeSection from './components/ResumeSection.vue'
import ServicesSection from './components/ServicesSection.vue'

const activeSection = ref('Home')
const menuOpen = ref(false)
const scrolled = ref(false)

function handleScroll() {
  scrolled.value = window.scrollY > 40
}

function scrollToSection(sectionName) {
  const target = document.getElementById(sectionName.toLowerCase())

  if (target) {
    target.scrollIntoView({ behavior: 'smooth' })
  }

  activeSection.value = sectionName
  menuOpen.value = false
}

onMounted(() => {
  handleScroll()
  window.addEventListener('scroll', handleScroll)
})

onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll)
})
</script>

<template>
  <div class="app-shell">
    <AppHeader
      :active-section="activeSection"
      :menu-open="menuOpen"
      :scrolled="scrolled"
      @navigate="scrollToSection"
      @toggle-menu="menuOpen = !menuOpen"
    />

    <main>
      <HeroSection @navigate="scrollToSection" />
      <AboutSection />
      <ResumeSection />
      <ServicesSection />
      <PortfolioSection />
      <ContactSection />
    </main>

    <AppFooter />
  </div>
</template>

<style>
:root {
  --color-bg: #0d1220;
  --color-bg-soft: #0a0f1a;
  --color-panel: #131928;
  --color-text: #f0f2f8;
  --color-muted: #8a94a8;
  --color-accent: #9b2335;
  --color-accent-dark: #7d1c2b;
  --font-body: 'Inter', system-ui, sans-serif;
  --font-display: 'Playfair Display', Georgia, serif;
}

* {
  box-sizing: border-box;
}

html {
  scroll-behavior: smooth;
}

body {
  margin: 0;
  min-width: 320px;
  background: var(--color-bg);
  color: var(--color-text);
  font-family: var(--font-body);
}

button,
input,
textarea {
  font: inherit;
}

button {
  cursor: pointer;
}

a {
  color: inherit;
  text-decoration: none;
}

.app-shell {
  min-height: 100vh;
  width: 100%;
  overflow-x: hidden;
  background: var(--color-bg);
}

.container {
  width: min(100% - 48px, 1280px);
  margin: 0 auto;
}

.section {
  padding: 96px 0;
}

.section--dark {
  background: var(--color-bg-soft);
}

.section--base {
  background: var(--color-bg);
}

.button {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  gap: 8px;
  border: 0;
  border-radius: 2px;
  padding: 12px 28px;
  color: #fff;
  background: var(--color-accent);
  font-size: 0.82rem;
  letter-spacing: 0.12em;
  text-transform: uppercase;
  transition:
    background 180ms ease,
    border-color 180ms ease,
    color 180ms ease,
    transform 180ms ease;
}

.button:hover {
  background: var(--color-accent-dark);
}

.button--ghost {
  border: 1px solid rgba(155, 35, 53, 0.5);
  color: var(--color-accent);
  background: transparent;
}

.button--ghost:hover {
  border-color: var(--color-accent);
  background: rgba(155, 35, 53, 0.08);
}

.icon-box {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  width: 40px;
  height: 40px;
  border: 1px solid rgba(155, 35, 53, 0.25);
  border-radius: 2px;
  color: var(--color-accent);
  background: rgba(155, 35, 53, 0.1);
}

@media (max-width: 720px) {
  .container {
    width: min(100% - 32px, 1280px);
  }

  .section {
    padding: 72px 0;
  }
}
</style>
