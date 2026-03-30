<script setup>
import { ref, onMounted, onUnmounted, computed } from 'vue'
import Avatar1Img from '@/assets/images/Jorge.jpg'

const testimonials = [
  {
    id: 1,
    text: 'Ricardo trabajó con nosotros como desarrollador frontend. Enriqueció el proyecto con su profunda experiencia técnica y apreciamos mucho sus habilidades como jugador de equipo.',
    name: 'Jorge Eduardo',
    role: 'Arquitecto',
    company: 'UVM',
    avatar: Avatar1Img,
    stars: 5,
  },
  {
    id: 2,
    text: 'Ricardo hizo una contribución importante al progreso del producto y, como miembro del equipo, enriqueció el trabajo colaborativo. Creó gran parte de la base que nuestros usuarios disfrutan hoy.',
    name: 'Denise Tobian',
    role: 'Product Owner',
    company: 'ProSiebenSat.1 Tech Solutions',
    avatar: 'https://images.unsplash.com/photo-1438761681033-6461ffad8d80?q=80&w=100&auto=format&fit=crop',
    stars: 5,
  },
  {
    id: 3,
    text: 'Ricardo trabajó como empleado fijo en nuestra empresa y siempre realizó un trabajo absolutamente excelente. Solo puedo recomendarlo sin reservas.',
    name: 'Thomas Müller',
    role: 'Head of Department',
    company: 'Audi Mobility — jambit GmbH',
    avatar: 'https://images.unsplash.com/photo-1472099645785-5658abf4ff4e?q=80&w=100&auto=format&fit=crop',
    stars: 5,
  },
  // {
  //   id: 4,
  //   text: 'Trabajar con Michael fue una experiencia excepcional. Su atención al detalle y su capacidad para traducir diseños complejos en código limpio superó todas nuestras expectativas.',
  //   name: 'Laura Martínez',
  //   role: 'CTO',
  //   company: 'Startup Fintech MX',
  //   avatar: 'https://images.unsplash.com/photo-1534528741775-53994a69daeb?q=80&w=100&auto=format&fit=crop',
  //   stars: 5,
  // },
  // {
  //   id: 5,
  //   text: 'La calidad del código entregado por Michael es impecable. Documentación clara, componentes reutilizables y siempre dispuesto a ir más allá para asegurar el éxito del proyecto.',
  //   name: 'Marcos Oliveira',
  //   role: 'Engineering Manager',
  //   company: 'TechCorp Brasil',
  //   avatar: 'https://images.unsplash.com/photo-1507003211169-0a1dd7228f2d?q=80&w=100&auto=format&fit=crop',
  //   stars: 5,
  // },
]

// Carrusel con auto-play
const current = ref(0)
const isAnimating = ref(false)
const direction = ref(1) // 1 = forward, -1 = backward
let autoTimer = null

const total = testimonials.length

const prev = computed(() => (current.value - 1 + total) % total)
const next = computed(() => (current.value + 1) % total)

function goTo(index, dir = 1) {
  if (isAnimating.value) return
  direction.value = dir
  isAnimating.value = true
  current.value = index
  setTimeout(() => { isAnimating.value = false }, 500)
  resetTimer()
}

function goNext() { goTo(next.value, 1) }
function goPrev() { goTo(prev.value, -1) }

function startTimer() {
  autoTimer = setInterval(goNext, 5000)
}

function resetTimer() {
  clearInterval(autoTimer)
  startTimer()
}

// Visibilidad header
const headerRef = ref(null)
const headerVisible = ref(false)
let headerObs = null

onMounted(() => {
  startTimer()

  headerObs = new IntersectionObserver(
    ([e]) => { if (e.isIntersecting) headerVisible.value = true },
    { threshold: 0.3 }
  )
  if (headerRef.value) headerObs.observe(headerRef.value)
})

onUnmounted(() => {
  clearInterval(autoTimer)
  headerObs?.disconnect()
})

// Swipe touch
const touchStart = ref(0)
function onTouchStart(e) { touchStart.value = e.touches[0].clientX }
function onTouchEnd(e) {
  const delta = touchStart.value - e.changedTouches[0].clientX
  if (Math.abs(delta) > 40) delta > 0 ? goNext() : goPrev()
}
</script>

<template>
  <section id="testimonials" class="tm-section section">
    <div class="container">

      <!-- Header -->
      <div class="tm-header" ref="headerRef" :class="{ 'tm-header--in': headerVisible }">
        <span class="tm-eyebrow">Testimonios</span>
        <h2 class="tm-title">Lo que dicen de mí</h2>
        <p class="tm-sub">Opiniones de personas con las que he tenido el placer de colaborar.</p>
      </div>

      <!-- Carrusel -->
      <div class="tm-carousel" @touchstart="onTouchStart" @touchend="onTouchEnd">
        <!-- Cards visibles: prev (difuminada) · active · next (difuminada) -->
        <div class="tm-track">

          <!-- Card anterior (decorativa) -->
          <div class="tm-card tm-card--side tm-card--prev">
            <p class="tm-quote">{{ testimonials[prev].text }}</p>
            <div class="tm-author">
              <img :src="testimonials[prev].avatar" :alt="testimonials[prev].name" class="tm-avatar" />
              <div>
                <span class="tm-name">{{ testimonials[prev].name }}</span>
                <span class="tm-role">{{ testimonials[prev].role }}</span>
              </div>
            </div>
          </div>

          <!-- Card activa -->
          <div class="tm-card tm-card--active" :class="{ 'tm-card--animating': isAnimating }">

            <!-- Estrellas -->
            <div class="tm-stars" :aria-label="`${testimonials[current].stars} estrellas`">
              <svg v-for="s in 5" :key="s" class="tm-star"
                :class="{ 'tm-star--filled': s <= testimonials[current].stars }" viewBox="0 0 24 24" width="14"
                height="14">
                <polygon
                  points="12 2 15.09 8.26 22 9.27 17 14.14 18.18 21.02 12 17.77 5.82 21.02 7 14.14 2 9.27 8.91 8.26 12 2" />
              </svg>
            </div>

            <p class="tm-quote tm-quote--main">{{ testimonials[current].text }}</p>

            <div class="tm-author tm-author--main">
              <div class="tm-avatar-wrap">
                <img :src="testimonials[current].avatar" :alt="testimonials[current].name"
                  class="tm-avatar tm-avatar--main" />
                <span class="tm-avatar-ring"></span>
              </div>
              <div class="tm-author-info">
                <span class="tm-name tm-name--main">{{ testimonials[current].name }}</span>
                <span class="tm-role">{{ testimonials[current].role }}</span>
                <span class="tm-company">{{ testimonials[current].company }}</span>
              </div>
            </div>
          </div>

          <!-- Card siguiente (decorativa) -->
          <div class="tm-card tm-card--side tm-card--next">
            <p class="tm-quote">{{ testimonials[next].text }}</p>
            <div class="tm-author">
              <img :src="testimonials[next].avatar" :alt="testimonials[next].name" class="tm-avatar" />
              <div>
                <span class="tm-name">{{ testimonials[next].name }}</span>
                <span class="tm-role">{{ testimonials[next].role }}</span>
              </div>
            </div>
          </div>

        </div>

        <!-- Controles -->
        <div class="tm-controls">
          <button class="tm-btn" @click="goPrev" aria-label="Anterior">
            <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" viewBox="0 0 24 24" fill="none"
              stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round">
              <path d="M15 18l-6-6 6-6" />
            </svg>
          </button>

          <!-- Dots -->
          <div class="tm-dots" role="tablist">
            <button v-for="(_, i) in testimonials" :key="i" class="tm-dot" :class="{ 'tm-dot--active': i === current }"
              @click="goTo(i, i > current ? 1 : -1)" :aria-label="`Ir al testimonio ${i + 1}`" role="tab"
              :aria-selected="i === current"></button>
          </div>

          <button class="tm-btn" @click="goNext" aria-label="Siguiente">
            <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" viewBox="0 0 24 24" fill="none"
              stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round">
              <path d="M9 18l6-6-6-6" />
            </svg>
          </button>
        </div>

        <!-- Barra de progreso auto-play -->
        <div class="tm-progress" aria-hidden="true">
          <div class="tm-progress-bar" :key="current"></div>
        </div>

      </div>
    </div>
  </section>
</template>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Syne:wght@700;800&family=Outfit:wght@300;400;500&family=Fraunces:ital,opsz,wght@1,9..144,300&display=swap');

/* ── Section ─────────────────────────────────────────────── */
.tm-section {
  overflow: hidden;
}

/* ── Header ──────────────────────────────────────────────── */
.tm-header {
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
  gap: 0.5rem;
  margin-bottom: 4rem;
  opacity: 0;
  transform: translateY(16px);
  transition: opacity 0.65s ease, transform 0.65s ease;
}

.tm-header--in {
  opacity: 1;
  transform: translateY(0);
}

.tm-eyebrow {
  font-family: 'Outfit', sans-serif;
  font-size: 0.72rem;
  font-weight: 500;
  letter-spacing: 0.18em;
  text-transform: uppercase;
  color: var(--green-9);
}

.tm-title {
  font-family: 'Syne', sans-serif;
  font-size: clamp(2rem, 4vw, 3rem);
  font-weight: 800;
  letter-spacing: -0.03em;
  color: var(--gray-12);
  margin: 0;
}

.tm-sub {
  font-family: 'Outfit', sans-serif;
  font-size: 0.975rem;
  color: var(--gray-11);
  font-weight: 300;
  margin: 0;
  max-width: 500px;
}

/* ── Carousel ────────────────────────────────────────────── */
.tm-carousel {
  position: relative;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 2rem;
}

/* ── Track: 3 cards visibles ─────────────────────────────── */
.tm-track {
  display: grid;
  grid-template-columns: 1fr 1.45fr 1fr;
  gap: 1.25rem;
  align-items: center;
  width: 100%;
  max-width: 960px;
}

/* ── Card base ───────────────────────────────────────────── */
.tm-card {
  background: var(--gray-2);
  border: 1px solid var(--gray-8);
  border-radius: 18px;
  padding: 1.75rem;
  display: flex;
  flex-direction: column;
  gap: 1rem;
  position: relative;
  overflow: hidden;
}

/* ── Cards laterales (prev / next) ──────────────────────── */
.tm-card--side {
  opacity: 0.35;
  filter: blur(1px);
  transform: scale(0.94);
  pointer-events: none;
  user-select: none;
  transition: opacity 0.4s ease, filter 0.4s ease, transform 0.4s ease;
}

/* ── Card activa ─────────────────────────────────────────── */
.tm-card--active {
  border-color: rgba(0, 230, 118, 0.18);
  box-shadow:
    0 0 0 1px rgba(0, 230, 118, 0.08),
    0 20px 60px rgba(0, 0, 0, 0.4);
  transition: opacity 0.4s ease, transform 0.4s ease;
}

/* Fade breve al cambiar */
.tm-card--animating {
  opacity: 0.7;
  transform: scale(0.98);
}

/* ── Estrellas ───────────────────────────────────────────── */
.tm-stars {
  display: flex;
  gap: 0.2rem;
}

.tm-star {
  fill: var(--gray-8);
  stroke: none;
  transition: fill 0.2s ease;
}

.tm-star--filled {
  fill: #f59e0b;
}

/* ── Quote text ──────────────────────────────────────────── */
.tm-quote {
  font-family: 'Outfit', sans-serif;
  font-size: 0.8rem;
  color: var(--gray-11);
  line-height: 1.65;
  margin: 0;
  font-weight: 300;
  /* Limitar a 3 líneas en cards laterales */
  display: -webkit-box;
  -webkit-line-clamp: 3;
  -webkit-box-orient: vertical;
  overflow: hidden;
}

.tm-quote--main {
  font-size: 0.96rem;
  color: var(--gray-12);
  font-weight: 400;
  -webkit-line-clamp: unset;
  overflow: visible;
  line-height: 1.75;
}

/* ── Author ──────────────────────────────────────────────── */
.tm-author {
  display: flex;
  align-items: center;
  gap: 0.75rem;
  margin-top: auto;
}

.tm-author--main {
  gap: 1rem;
}

.tm-avatar-wrap {
  position: relative;
  flex-shrink: 0;
}

.tm-avatar {
  width: 36px;
  height: 36px;
  border-radius: 50%;
  object-fit: cover;
  display: block;
  border: 1.5px solid var(--gray-8);
}

.tm-avatar--main {
  width: 48px;
  height: 48px;
  /* border-color: rgba(0, 230, 118, 0.25); */
  border-color: var(--green-8);
}

/* Anillo verde avatar principal */
.tm-avatar-ring {
  position: absolute;
  inset: -3px;
  border-radius: 50%;
  /* border: 1.5px solid rgba(0, 230, 118, 0.3); */
  border: 1.5px solid var(--green-7);
  animation: avatar-ring 3s ease-in-out infinite alternate;
}

@keyframes avatar-ring {
  from {
    opacity: 0.4;
    transform: scale(1);
  }

  to {
    opacity: 1;
    transform: scale(1.05);
  }
}

.tm-author-info {
  display: flex;
  flex-direction: column;
  gap: 0.1rem;
}

.tm-name {
  font-family: 'Outfit', sans-serif;
  font-size: 0.78rem;
  font-weight: 600;
  color: var(--gray-12);
  line-height: 1.2;
}

.tm-name--main {
  font-family: 'Syne', sans-serif;
  font-size: 0.9rem;
  font-weight: 700;
  letter-spacing: -0.01em;
}

.tm-role {
  font-family: 'Outfit', sans-serif;
  font-size: 0.72rem;
  color: var(--gray-11);
  font-weight: 400;
  line-height: 1.3;
}

.tm-company {
  font-family: 'Outfit', sans-serif;
  font-size: 0.68rem;
  color: var(--green-9);
  font-weight: 500;
  opacity: 0.85;
}

/* ── Controles ───────────────────────────────────────────── */
.tm-controls {
  display: flex;
  align-items: center;
  gap: 1.25rem;
}

.tm-btn {
  width: 38px;
  height: 38px;
  border-radius: 50%;
  border: 1px solid var(--gray-8);
  background: transparent;
  color: var(--gray-11);
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
  transition: color 0.2s ease, border-color 0.2s ease, background 0.2s ease, transform 0.2s ease;
  flex-shrink: 0;
}

.tm-btn:hover {
  color: var(--gray-12);
  border-color: rgba(255, 255, 255, 0.2);
  background: rgba(255, 255, 255, 0.04);
  transform: scale(1.08);
}

.tm-btn:active {
  transform: scale(0.92);
}

/* Dots */
.tm-dots {
  display: flex;
  gap: 0.45rem;
  align-items: center;
}

.tm-dot {
  width: 6px;
  height: 6px;
  border-radius: 50%;
  background: var(--gray-8);
  border: none;
  cursor: pointer;
  padding: 0;
  transition: background 0.3s ease, transform 0.3s ease, width 0.3s ease;
}

.tm-dot--active {
  background: var(--green-8);
  width: 22px;
  border-radius: 99px;
  box-shadow: 0 0 8px rgba(0, 230, 118, 0.5);
}

/* ── Barra de progreso ───────────────────────────────────── */
.tm-progress {
  width: 100%;
  max-width: 960px;
  height: 1px;
  background: var(--gray-8);
  border-radius: 99px;
  overflow: hidden;
}

.tm-progress-bar {
  height: 100%;
  width: 0%;
  background: linear-gradient(to right, var(--green-8), rgba(0, 230, 118, 0.4));
  border-radius: 99px;
  animation: progress-fill 5s linear forwards;
}

@keyframes progress-fill {
  from {
    width: 0%;
  }

  to {
    width: 100%;
  }
}

/* ── Responsive ──────────────────────────────────────────── */
@media (max-width: 768px) {
  .tm-track {
    grid-template-columns: 1fr;
  }

  .tm-card--side {
    display: none;
  }

  .tm-card--active {
    max-width: 100%;
  }
}
</style>