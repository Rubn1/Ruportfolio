<script setup>
import { navLinks } from '../data/portfolioData'

defineProps({
  activeSection: {
    type: String,
    required: true,
  },
  menuOpen: {
    type: Boolean,
    required: true,
  },
  scrolled: {
    type: Boolean,
    required: true,
  },
})

defineEmits(['navigate', 'toggle-menu'])
</script>

<template>
  <header class="site-header" :class="{ 'site-header--scrolled': scrolled }">
    <nav class="container nav">
      <button class="brand" type="button" @click="$emit('navigate', 'Home')">Rubn Mercy</button>

      <ul class="nav__links">
        <li v-for="link in navLinks" :key="link">
          <button
            type="button"
            class="nav__link"
            :class="{ 'nav__link--active': activeSection === link }"
            @click="$emit('navigate', link)"
          >
            {{ link }}
          </button>
        </li>
      </ul>

      <div class="nav__phone">
        <span aria-hidden="true">☎</span>
        <span>+250 000 000 000</span>
      </div>

      <button
        type="button"
        class="nav__toggle"
        :aria-expanded="menuOpen"
        aria-label="Toggle navigation"
        @click="$emit('toggle-menu')"
      >
        {{ menuOpen ? '×' : '☰' }}
      </button>
    </nav>

    <div v-if="menuOpen" class="mobile-menu">
      <button
        v-for="link in navLinks"
        :key="link"
        type="button"
        class="mobile-menu__link"
        :class="{ 'mobile-menu__link--active': activeSection === link }"
        @click="$emit('navigate', link)"
      >
        {{ link }}
      </button>
    </div>
  </header>
</template>

<style scoped>
.site-header {
  position: fixed;
  inset: 0 0 auto;
  z-index: 50;
  background: transparent;
  transition:
    background 220ms ease,
    border-color 220ms ease,
    backdrop-filter 220ms ease;
}

.site-header--scrolled {
  border-bottom: 1px solid rgba(155, 35, 53, 0.15);
  background: rgba(13, 18, 32, 0.96);
  backdrop-filter: blur(12px);
}

.nav {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding-block: 16px;
}

.brand,
.nav__link,
.nav__toggle,
.mobile-menu__link {
  border: 0;
  background: transparent;
}

.brand {
  color: var(--color-accent);
  font-family: var(--font-display);
  font-size: 1.25rem;
  letter-spacing: 0.08em;
}

.nav__links {
  display: flex;
  align-items: center;
  gap: 32px;
  padding: 0;
  margin: 0;
  list-style: none;
}

.nav__link,
.mobile-menu__link {
  color: var(--color-muted);
  font-size: 0.78rem;
  letter-spacing: 0.14em;
  text-transform: uppercase;
  transition: color 180ms ease;
}

.nav__link:hover,
.nav__link--active,
.mobile-menu__link:hover,
.mobile-menu__link--active {
  color: var(--color-accent);
}

.nav__phone {
  display: flex;
  align-items: center;
  gap: 10px;
  color: var(--color-muted);
  font-size: 0.88rem;
}

.nav__phone span:first-child {
  color: var(--color-accent);
}

.nav__toggle {
  display: none;
  color: var(--color-accent);
  font-size: 1.5rem;
  line-height: 1;
}

.mobile-menu {
  display: none;
}

@media (max-width: 820px) {
  .nav__links,
  .nav__phone {
    display: none;
  }

  .nav__toggle {
    display: inline-flex;
  }

  .mobile-menu {
    display: flex;
    flex-direction: column;
    gap: 16px;
    padding: 4px 24px 24px;
    background: rgba(13, 18, 32, 0.98);
  }

  .mobile-menu__link {
    align-self: flex-start;
  }
}
</style>
