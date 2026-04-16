<script setup lang="ts">
import { ref, onMounted, onUnmounted } from 'vue'

import desktopBanner1 from '@/assets/images/desktop/banner1.png'
import desktopBanner2 from '@/assets/images/desktop/banner2.png'
import desktopBanner3 from '@/assets/images/desktop/banner3.png'
import desktopBanner4 from '@/assets/images/desktop/banner4.png'
import mobileBanner1 from '@/assets/images/mobile/banner1.jpeg'
import mobileBanner2 from '@/assets/images/mobile/banner2.jpeg'
import mobileBanner3 from '@/assets/images/mobile/banner3.jpeg'
import mobileBanner4 from '@/assets/images/mobile/banner4.jpeg'

const slides = [
  { desktop: desktopBanner1, mobile: mobileBanner1, alt: 'LC Assessoria de Seguros e Previdência' },
  { desktop: desktopBanner2, mobile: mobileBanner2, alt: 'Está afastado do trabalho?' },
  { desktop: desktopBanner3, mobile: mobileBanner3, alt: 'Ficou com sequelas após um acidente?' },
  { desktop: desktopBanner4, mobile: mobileBanner4, alt: 'Quer garantir um futuro tranquilo?' },
]

const current = ref(0)
let interval: ReturnType<typeof setInterval> | null = null

function next() {
  current.value = (current.value + 1) % slides.length
}

function prev() {
  current.value = (current.value - 1 + slides.length) % slides.length
}

function goTo(index: number) {
  current.value = index
  resetAutoplay()
}

function resetAutoplay() {
  if (interval) clearInterval(interval)
  interval = setInterval(next, 5000)
}

onMounted(() => {
  interval = setInterval(next, 5000)
})

onUnmounted(() => {
  if (interval) clearInterval(interval)
})
</script>

<template>
  <section id="inicio" class="hero">
    <div class="carousel">
      <div
        v-for="(slide, index) in slides"
        :key="index"
        class="slide"
        :class="{ active: index === current }"
      >
        <picture>
          <source :srcset="slide.mobile" media="(max-width: 768px)" />
          <img :src="slide.desktop" :alt="slide.alt" class="slide-img" />
        </picture>
      </div>

      <button class="carousel-btn carousel-prev" @click="prev" aria-label="Anterior">
        <svg
          width="24"
          height="24"
          viewBox="0 0 24 24"
          fill="none"
          stroke="currentColor"
          stroke-width="2.5"
          stroke-linecap="round"
          stroke-linejoin="round"
        >
          <polyline points="15 18 9 12 15 6" />
        </svg>
      </button>
      <button class="carousel-btn carousel-next" @click="next" aria-label="Próximo">
        <svg
          width="24"
          height="24"
          viewBox="0 0 24 24"
          fill="none"
          stroke="currentColor"
          stroke-width="2.5"
          stroke-linecap="round"
          stroke-linejoin="round"
        >
          <polyline points="9 18 15 12 9 6" />
        </svg>
      </button>

      <div class="carousel-dots">
        <button
          v-for="(_, index) in slides"
          :key="index"
          class="dot"
          :class="{ active: index === current }"
          @click="goTo(index)"
          :aria-label="`Slide ${index + 1}`"
        ></button>
      </div>
    </div>
  </section>
</template>

<style scoped>
.hero {
  margin-top: var(--header-height);
}

.carousel {
  position: relative;
  width: 100%;
  margin: 0 auto;
  overflow: hidden;
}

.slide {
  position: absolute;
  inset: 0;
  opacity: 0;
  transition: opacity 0.6s ease;
}

.slide.active {
  position: relative;
  opacity: 1;
}

.slide-img {
  width: 100%;
  height: auto;
  display: block;
}

.carousel-btn {
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  width: 48px;
  height: 48px;
  border-radius: 50%;
  background-color: rgba(255, 255, 255, 0.85);
  border: none;
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
  transition: var(--transition);
  z-index: 2;
  color: var(--color-dark);
}

.carousel-btn:hover {
  background-color: var(--color-primary);
  color: var(--color-text-light);
}

.carousel-prev {
  left: 16px;
}

.carousel-next {
  right: 16px;
}

.carousel-dots {
  position: absolute;
  bottom: 20px;
  left: 50%;
  transform: translateX(-50%);
  display: flex;
  gap: 10px;
  z-index: 2;
}

.dot {
  width: 12px;
  height: 12px;
  border-radius: 50%;
  border: 2px solid var(--color-text-light);
  background-color: transparent;
  cursor: pointer;
  transition: var(--transition);
  padding: 0;
}

.dot.active {
  background-color: var(--color-primary);
  border-color: var(--color-primary);
}

.dot:hover {
  background-color: rgba(255, 255, 255, 0.6);
}

@media (max-width: 768px) {
  .carousel {
    width: 100%;
  }

  .carousel-btn {
    width: 36px;
    height: 36px;
  }

  .carousel-btn svg {
    width: 18px;
    height: 18px;
  }

  .carousel-prev {
    left: 8px;
  }

  .carousel-next {
    right: 8px;
  }

  .carousel-dots {
    bottom: 12px;
  }

  .dot {
    width: 10px;
    height: 10px;
  }
}
</style>
