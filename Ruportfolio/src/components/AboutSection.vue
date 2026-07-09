<script setup>
import ImageWithFallback from './ImageWithFallback.vue'
import SectionHeading from './SectionHeading.vue'
import profileImage from '../assets/image1.jpeg'

const details = [
  ['Email', 'mercy@example.com'],
  ['Skills', 'React, Vue, Laravel, Photoshop, Illustrator, After Effects'],
  ['Language', 'English, French'],
  ['Freelance', 'Available'],
]
</script>

<template>
  <section id="about" class="section section--base">
    <div class="container">
      <SectionHeading title="About Me" />

      <div class="about">
        <div class="about__photo">
          <div class="about__photo-frame">
            <ImageWithFallback :src="profileImage" alt="About photo" class="about__image" />
          </div>
        </div>

        <div class="about__content">
          <h3>Hi There! I'm Mercy</h3>
          <p class="about__role">Software Engineer &amp; Creative Designer</p>
          <p class="about__text">
            I'm Ndabunguye Mercy - a Software Engineer who also brings a creative edge. I build
            modern web and mobile applications, design stunning visuals, shoot professional photos,
            and create motion graphics. I combine technical precision with artistic vision to
            deliver work that truly stands out.
          </p>

          <dl class="about__details">
            <div v-for="[label, value] in details" :key="label">
              <dt>{{ label }}</dt>
              <dd>: {{ value }}</dd>
            </div>
          </dl>

          <button type="button" class="button">
            <span aria-hidden="true">↓</span>
            Download CV
          </button>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.about {
  display: grid;
  grid-template-columns: minmax(260px, 0.9fr) minmax(0, 1.1fr);
  align-items: center;
  gap: 64px;
  margin-top: 56px;
}

.about__photo {
  display: flex;
  justify-content: center;
}

.about__photo-frame {
  position: relative;
}

.about__photo-frame::before {
  position: absolute;
  right: -16px;
  bottom: -16px;
  width: 100%;
  height: 100%;
  border: 1px solid rgba(155, 35, 53, 0.3);
  border-radius: 2px;
  background: rgba(155, 35, 53, 0.15);
  content: '';
}

.about__image {
  position: relative;
  width: min(100%, 380px);
  height: 460px;
  border-radius: 2px;
  object-fit: cover;
  object-position: top;
  filter: brightness(0.92) contrast(1.05);
}

h3 {
  margin: 0 0 8px;
  color: var(--color-text);
  font-family: var(--font-display);
  font-size: 1.75rem;
}

.about__role {
  margin: 0 0 24px;
  color: var(--color-accent);
}

.about__text {
  margin: 0 0 32px;
  color: var(--color-muted);
  line-height: 1.75;
}

.about__details {
  display: grid;
  gap: 12px;
  margin: 0 0 32px;
}

.about__details div {
  display: flex;
  gap: 16px;
}

dt {
  flex: 0 0 96px;
  color: var(--color-accent);
  font-size: 0.9rem;
}

dd {
  margin: 0;
  color: var(--color-muted);
  font-size: 0.9rem;
}

@media (max-width: 820px) {
  .about {
    grid-template-columns: 1fr;
  }
}
</style>
