<script setup>
import SectionHeading from './SectionHeading.vue'
import { contactItems } from '../data/portfolioData'
</script>

<template>
  <section id="contact" class="section section--base">
    <div class="contact-container">
      <SectionHeading title="Contact" />

      <div class="contact">
        <div class="contact__info">
          <h3>Let's Work Together</h3>
          <p>
            Whether you need a website, mobile app, flyer design, photography, or motion graphics -
            I'm ready to bring your vision to life. Let's build something amazing together.
          </p>

          <div class="contact__items">
            <div v-for="item in contactItems" :key="item.label" class="contact__item">
              <span class="icon-box" aria-hidden="true">{{ item.icon }}</span>
              <span>{{ item.label }}</span>
            </div>
          </div>
        </div>

        <form class="contact__form" @submit.prevent>
          <input type="text" placeholder="Your Name" />
          <input type="email" placeholder="Your Email" />
          <input type="text" placeholder="Subject" />
          <textarea rows="5" placeholder="Your Message"></textarea>
          <button type="submit" class="button">Send Message</button>
        </form>
      </div>
    </div>
  </section>
</template>

<style scoped>
.contact-container {
  width: min(100% - 48px, 1024px);
  margin: 0 auto;
}

.contact {
  display: grid;
  grid-template-columns: minmax(0, 1fr) minmax(0, 1fr);
  gap: 64px;
  margin-top: 56px;
}

h3 {
  margin: 0 0 16px;
  color: var(--color-text);
  font-family: var(--font-display);
  font-size: 1.5rem;
}

p {
  margin: 0 0 32px;
  color: var(--color-muted);
  line-height: 1.75;
}

.contact__items,
.contact__form {
  display: grid;
  gap: 16px;
}

.contact__item {
  display: flex;
  align-items: center;
  gap: 16px;
  color: var(--color-muted);
  font-size: 0.9rem;
}

input,
textarea {
  width: 100%;
  border: 1px solid rgba(155, 35, 53, 0.2);
  border-radius: 2px;
  outline: 0;
  padding: 13px 16px;
  color: var(--color-text);
  background: var(--color-panel);
  font-size: 0.9rem;
  transition: border-color 180ms ease;
}

input:focus,
textarea:focus {
  border-color: var(--color-accent);
}

textarea {
  resize: vertical;
}

.contact__form .button {
  width: 100%;
}

@media (max-width: 820px) {
  .contact-container {
    width: min(100% - 32px, 1024px);
  }

  .contact {
    grid-template-columns: 1fr;
  }
}
</style>
