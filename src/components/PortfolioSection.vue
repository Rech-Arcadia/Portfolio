<script>
import { markRaw } from 'vue'
import PencilHeartIcon from '../assets/icons/pencil-heart.vue'
import ComponentsIcon from '../assets/icons/components.vue'
import ImageGenerationIcon from '../assets/icons/image-generation.vue'
import { projects } from '../data/portfolioData.js'

export default {
  name: 'PortfolioSection',
  components: {
    PencilHeartIcon,
    ComponentsIcon,
    ImageGenerationIcon,
  },
  data() {
    return {
      visible: false,
      needs: [
        { text: 'Un Junior Developer especializado en Design Web con +1 año de experiencia.', tag: 'Experiencia', icon: markRaw(PencilHeartIcon) },
        { text: 'Apoyo para construir una aplicación web compleja, moderna y escalable.', tag: 'Arquitectura', icon: markRaw(ComponentsIcon) },
        { text: 'Un desarrollador que prioriza código limpio, bien documentado y de alta calidad.', tag: 'Calidad', icon: markRaw(ImageGenerationIcon) },
      ],
      stats: [
        { label: 'Años exp.', value: 0, target: 1 },
        { label: 'Proyectos', value: 0, target: 5 },
        { label: 'Rating', value: 0, target: 4.5 },
      ],
    }
  },
  methods: {
    animateStats() {
      this.stats.forEach((stat) => {
        const increment = stat.target / 250

        const update = () => {
          if (stat.value < stat.target) {
            stat.value += increment
            if (stat.value > stat.target) stat.value = stat.target
            requestAnimationFrame(update)
          }
        }
        update()
      })
    },
    formatStat(stat) {
      if (stat.target < 5) {
        return Math.round(stat.value)
      }

      if (stat.target % 1 !== 0) {
        return stat.value.toFixed(1)
      }

      return Math.round(stat.value)
    },
  },
  mounted() {
    const observer = new IntersectionObserver(
      ([entry]) => { if (entry.isIntersecting) this.visible = true, this.animateStats() },
      { threshold: 0.20 }
    )
    const el = document.getElementById('about')
    if (el) observer.observe(el)
  },
};
</script>

<template>
  <section id="about" class="ps-section section">
    <div class="container ps-grid">

      <!-- ── Sidebar ──────────────────────────────────── -->
      <aside class="ps-sidebar" :class="{ visible }">

        <div class="ps-photo-wrap">
          <img src="/src/assets/images/Yo-ese-2.png" alt="Ricardo Hoffmann" class="ps-photo" />
          <div class="ps-photo-badge">
            <span class="ps-dot"></span>
            Disponible
          </div>
        </div>

        <div class="ps-sidebar-body">
          <p class="ps-role">Freelancer · Content Creator · Web Developer</p>

          <div class="ps-quick-stats">
            <div class="ps-container" v-for="item in stats" :key="item.label">
              <div class="ps-qstat">
                <span class="ps-qstat-val">+{{ formatStat(item) }}</span>
                <span class="ps-qstat-lbl">{{ item.label }}</span>
              </div>
              <div v-if="item !== stats[stats.length - 1]" class="ps-qstat-sep"></div>
            </div>
          </div>

          <!-- <audio autoplay controls>
            <source src="../assets/JH.mp3" type="audio/mpeg">
            Tu navegador no soporta elementos de audio.
          </audio> -->

          <a href="mailto:RicardoArAv@outlook.com" class="ps-hire-btn">
            <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none"
              stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"
              class="icon icon-tabler icons-tabler-outline icon-tabler-mail-forward">
              <path stroke="none" d="M0 0h24v24H0z" fill="none" />
              <path d="M12 18h-7a2 2 0 0 1 -2 -2v-10a2 2 0 0 1 2 -2h14a2 2 0 0 1 2 2v7.5" />
              <path d="M3 6l9 6l9 -6" />
              <path d="M15 18h6" />
              <path d="M18 15l3 3l-3 3" />
            </svg>
            Contactame
            <span class="ps-hire-shimmer"></span>
          </a>

          <div class="ps-socials">
            <a href="https://github.com/Rech-Arcadia" target="_blank" class="ps-social" aria-label="GitHub">
              <svg viewBox="0 0 24 24" width="16" height="16" fill="currentColor">
                <path
                  d="M12 2C6.477 2 2 6.484 2 12.017c0 4.425 2.865 8.18 6.839 9.504.5.092.682-.217.682-.483 0-.237-.008-.868-.013-1.703-2.782.605-3.369-1.343-3.369-1.343-.454-1.158-1.11-1.466-1.11-1.466-.908-.62.069-.608.069-.608 1.003.07 1.531 1.032 1.531 1.032.892 1.53 2.341 1.088 2.91.832.092-.647.35-1.088.636-1.338-2.22-.253-4.555-1.113-4.555-4.951 0-1.093.39-1.988 1.029-2.688-.103-.253-.446-1.272.098-2.65 0 0 .84-.27 2.75 1.026A9.564 9.564 0 0 1 12 6.844c.85.004 1.705.115 2.504.337 1.909-1.296 2.747-1.027 2.747-1.027.546 1.379.202 2.398.1 2.651.64.7 1.028 1.595 1.028 2.688 0 3.848-2.339 4.695-4.566 4.943.359.309.678.92.678 1.855 0 1.338-.012 2.419-.012 2.747 0 .268.18.58.688.482A10.019 10.019 0 0 0 22 12.017C22 6.484 17.522 2 12 2z" />
              </svg>
              GitHub
            </a>
            <a href="https://www.linkedin.com/in/ricardo-arcadia/" target="_blank" class="ps-social"
              aria-label="LinkedIn">
              <svg viewBox="0 0 24 24" width="16" height="16" fill="currentColor">
                <path
                  d="M20.447 20.452h-3.554v-5.569c0-1.328-.027-3.037-1.852-3.037-1.853 0-2.136 1.445-2.136 2.939v5.667H9.351V9h3.414v1.561h.046c.477-.9 1.637-1.85 3.37-1.85 3.601 0 4.267 2.37 4.267 5.455v6.286zM5.337 7.433a2.062 2.062 0 0 1-2.063-2.065 2.064 2.064 0 1 1 2.063 2.065zm1.782 13.019H3.555V9h3.564v11.452zM22.225 0H1.771C.792 0 0 .774 0 1.729v20.542C0 23.227.792 24 1.771 24h20.451C23.2 24 24 23.227 24 22.271V1.729C24 .774 23.2 0 22.222 0h.003z" />
              </svg>
              LinkedIn
            </a>
          </div>
        </div>
      </aside>

      <!-- ── Contenido principal ──────────────────────── -->
      <div class="ps-content" :class="{ visible }">

        <!-- Proyectos -->
        <div class="ps-block">
          <div class="ps-block-header">
            <span class="ps-block-eyebrow">Sobre mí</span>
            <h3 class="ps-block-title">Hola, soy <span class="capsule-text">Ricardo</span> 👋🏻</h3>
          </div>

          <p>
            Soy un Ing. En Sistemas con especial interés en el desarrollo web - front-end. Tengo experiencia
            construyendo interfaces modernas, escalables y funcionales con Vue.js, Vuetify, JavaScript, PHP, HTML y CSS,
            aplicando principios de diseño responsivo y usabilidad.
          </p>
        </div>

        <!-- Divider -->
        <div class="ps-divider"></div>

        <!-- Necesidades -->
        <div class="ps-block">
          <div class="ps-block-header">
            <span class="ps-block-eyebrow">Servicios</span>
            <h3 class="ps-block-title">¿Necesitas…?</h3>
          </div>

          <ul class="ps-needs-list">
            <li v-for="(need, i) in needs" :key="i" class="ps-need-item">
              <div class="ps-need-check">
                <component :is="need.icon" width="18" height="18" />
              </div>
              <div class="ps-need-body">
                <span class="ps-need-tag">{{ need.tag }}</span>
                <p class="ps-need-text">{{ need.text }}</p>
              </div>
            </li>
          </ul>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Syne:wght@600;700;800&family=Outfit:wght@300;400;500&display=swap');

/* ── Section ─────────────────────────────────────────────── */
.ps-section {
  padding: 7rem 0;
}

/* ── Grid principal ──────────────────────────────────────── */
.ps-grid {
  display: grid;
  grid-template-columns: 280px 1fr;
  gap: 4rem;
  align-items: start;
}

/* ── Sidebar ─────────────────────────────────────────────── */
.ps-sidebar {
  position: sticky;
  top: 100px;
  opacity: 0;
  transform: translateX(-20px);
  transition: opacity 0.6s ease, transform 0.6s ease;
}

.ps-sidebar.visible {
  opacity: 1;
  transform: translateX(0);
}

/* Foto */
.ps-photo-wrap {
  position: relative;
  margin-bottom: 10px;
  transition: all 0.3s ease;
  border-radius: 28px;
}

.ps-photo-wrap:hover {
  padding: 1px;
  background: linear-gradient(135deg, var(--green-9), #00bfa5, #1de9b6, var(--green-9));
  mask-composite: exclude;
  transform: rotate(-1deg);
  animation: photo-glow 2s ease-in-out infinite;
}

@keyframes photo-glow {

  0%,
  100% {
    box-shadow: 0 0 8px rgba(0, 230, 118, 0.7);
  }

  50% {
    box-shadow: 0 0 14px rgba(0, 230, 118, 0.3);
  }
}

.ps-photo {
  width: 100%;
  aspect-ratio: 3 / 4;
  object-fit: cover;
  border-radius: 28px;
  display: block;
  border: 1px solid var(--gray-6);
}

.ps-photo-badge {
  position: absolute;
  top: 5%;
  right: 5%;
  display: flex;
  align-items: center;
  gap: 0.45rem;
  background: rgba(16, 16, 16, 0.82);
  backdrop-filter: blur(12px);
  border: 1px solid rgba(0, 230, 118, 0.2);
  border-radius: 50px;
  padding: 0.3rem 0.8rem;

  font-family: 'Outfit', sans-serif;
  font-size: 0.7rem;
  font-weight: 500;
  color: var(--green-9);
  white-space: nowrap;
}

.ps-dot {
  width: 7px;
  height: 7px;
  border-radius: 50%;
  background: var(--green-9);
  box-shadow: 0 0 8px rgba(0, 230, 118, 0.7);
  animation: dot-pulse 2s ease-in-out infinite;
  flex-shrink: 0;
}

@keyframes dot-pulse {

  0%,
  100% {
    box-shadow: 0 0 6px rgba(0, 230, 118, 0.7);
  }

  50% {
    box-shadow: 0 0 14px rgba(0, 230, 118, 0.3);
  }
}

/* Cuerpo sidebar */
.ps-sidebar-body {
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

.ps-wave {
  font-style: normal;
}

.ps-role {
  font-family: 'Outfit', sans-serif;
  font-size: 0.78rem;
  color: var(--gray-11);
  font-weight: 300;
  margin: 0;
  line-height: 1.5;
}

/* Stats rápidas */
.ps-quick-stats {
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 1rem;
  padding: 0.85rem 1rem;
  background: rgba(255, 255, 255, 0.02);
  border: 1px solid var(--gray-8);
  border-radius: 12px;
}

.ps-qstat {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.1rem;
  flex: 1;
}

.ps-container {
  display: flex;
  align-items: center;
  gap: 20px;
}

.ps-qstat-val {
  font-family: 'Syne', sans-serif;
  font-size: 1.1rem;
  font-weight: 700;
  color: var(--gray-12);
  line-height: 1;
}

.ps-qstat-lbl {
  font-family: 'Outfit', sans-serif;
  font-size: 0.62rem;
  color: var(--gray-11);
  letter-spacing: 0.04em;
  white-space: nowrap;
}

.ps-qstat-sep {
  width: 1px;
  height: 28px;
  background: var(--gray-8);
  flex-shrink: 0;
}

/* Botón hire */
.ps-hire-btn {
  position: relative;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 0.5rem;
  padding: 0.7rem 1rem;
  background: var(--green-9);
  color: #061208;
  font-family: 'Outfit', sans-serif;
  font-weight: 600;
  font-size: 0.875rem;
  border-radius: 50px;
  text-decoration: none;
  overflow: hidden;
  transition: transform 0.22s ease, box-shadow 0.22s ease;
}

.ps-hire-btn:hover {
  transform: translateY(-2px);
  box-shadow: 0 10px 30px rgba(0, 230, 118, 0.25);
}

.ps-hire-shimmer {
  position: absolute;
  top: 0;
  left: -60%;
  width: 40%;
  height: 100%;
  background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.3), transparent);
  transform: skewX(-20deg);
  animation: shimmer 3.5s infinite 1s;
}

@keyframes shimmer {
  0% {
    left: -60%;
  }

  40% {
    left: 130%;
  }

  100% {
    left: 130%;
  }
}

/* Redes sociales */
.ps-socials {
  display: flex;
  gap: 0.6rem;
}

.ps-social {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 100%;
  height: 36px;
  gap: 10px;
  border-radius: 9px;
  border: 1px solid var(--gray-8);
  color: var(--gray-11);
  text-decoration: none;
  transition: color 0.2s ease, border-color 0.2s ease, background 0.2s ease;
}

.ps-social:hover {
  color: var(--gray-12);
  border-color: rgba(255, 255, 255, 0.2);
  background: rgba(255, 255, 255, 0.04);
}

/* ── Contenido ───────────────────────────────────────────── */
.ps-content {
  display: flex;
  flex-direction: column;
  gap: 20px;
  opacity: 0;
  transform: translateY(20px);
  transition: opacity 0.65s ease 0.1s, transform 0.65s ease 0.1s;
}

.ps-content.visible {
  opacity: 1;
  transform: translateY(0);
}

/* ── Bloques de contenido ────────────────────────────────── */
.ps-block {
  display: flex;
  flex-direction: column;
  gap: 30px;
}

.ps-block-header {
  display: flex;
  flex-direction: column;
  gap: 0.3rem;
}

.ps-block-eyebrow {
  font-family: 'Outfit', sans-serif;
  font-size: 0.68rem;
  font-weight: 500;
  letter-spacing: 0.14em;
  text-transform: uppercase;
  color: var(--green-9);
}

.ps-block-title {
  font-family: 'Syne', sans-serif;
  font-size: 1.6rem;
  font-weight: 700;
  color: var(--gray-12);
  margin: 0;
  letter-spacing: -0.02em;
}

.capsule-text {
  padding: 0.15rem 0.6rem;
  background: rgba(0, 230, 118, 0.1);
  color: var(--green-9);
  border-radius: 12px;
}

.ps-divider {
  height: 1px;
  background: var(--gray-8);
  opacity: 0.5;
}

@keyframes card-in {
  from {
    opacity: 0;
    transform: translateY(12px);
  }

  to {
    opacity: 1;
    transform: translateY(0);
  }
}

/* ── Lista de necesidades ────────────────────────────────── */
.ps-needs-list {
  display: flex;
  flex-direction: column;
  gap: 0.85rem;
  list-style: none;
  padding: 0;
  margin: 0;
}

.ps-need-item {
  display: flex;
  align-items: flex-start;
  gap: 0.85rem;
  padding: 1rem 1.1rem;
  background: rgba(255, 255, 255, 0.02);
  border: 1px solid var(--gray-8);
  border-radius: 12px;
  transition: background 0.2s ease, border-color 0.2s ease;
}

.ps-need-item:hover {
  background: rgba(0, 230, 118, 0.03);
  border-color: rgba(0, 230, 118, 0.15);
}

.ps-need-check {
  width: 26px;
  height: 26px;
  border-radius: 50%;
  background: var(--green-2);
  border: 1px solid rgba(0, 230, 118, 0.2);
  display: flex;
  align-items: center;
  justify-content: center;
  color: var(--green-9);
  flex-shrink: 0;
  margin-top: 1px;
}

.ps-need-body {
  display: flex;
  flex-direction: column;
  gap: 0.2rem;
}

.ps-need-tag {
  font-family: 'Outfit', sans-serif;
  font-size: 0.62rem;
  font-weight: 600;
  letter-spacing: 0.1em;
  text-transform: uppercase;
  color: var(--green-9);
}

.ps-need-text {
  font-family: 'Outfit', sans-serif;
  font-size: 0.875rem;
  color: var(--gray-11);
  line-height: 1.6;
  margin: 0;
}

/* ── CTA Banner ──────────────────────────────────────────── */
.ps-cta-banner {
  position: relative;
  display: flex;
  flex-wrap: wrap;
  align-items: center;
  justify-content: space-between;
  gap: 1.25rem;
  padding: 1.25rem 1.5rem;
  border-radius: 16px;
  border: 1px solid rgba(0, 230, 118, 0.15);
  overflow: hidden;
}

.ps-cta-banner-bg {
  position: absolute;
  inset: 0;
  background: radial-gradient(ellipse at 0% 50%, rgba(0, 230, 118, 0.07) 0%, transparent 60%);
  pointer-events: none;
}

.ps-cta-left {
  display: flex;
  align-items: center;
  gap: 0.85rem;
  position: relative;
}

.ps-cta-avatar-wrap {
  position: relative;
  flex-shrink: 0;
}

.ps-cta-avatar {
  width: 40px;
  height: 40px;
  border-radius: 50%;
  object-fit: cover;
  border: 2px solid rgba(0, 230, 118, 0.25);
}

/* .ps-cta-online {
  position: absolute;
  bottom: 1px;
  right: 1px;
  width: 10px;
  height: 10px;
  border-radius: 50%;
  background: var(--color-green);
  border: 2px solid var(--gray-1);
  box-shadow: 0 0 8px rgba(0, 230, 118, 0.6);
} */

.ps-cta-title {
  font-family: 'Outfit', sans-serif;
  font-size: 0.9rem;
  font-weight: 600;
  color: var(--gray-12);
  margin: 0;
}

.ps-cta-sub {
  font-family: 'Outfit', sans-serif;
  font-size: 0.72rem;
  color: var(--gray-11);
  margin: 0;
}

.ps-cta-actions {
  display: flex;
  gap: 0.75rem;
  flex-wrap: wrap;
  position: relative;
}

.ps-cta-ghost {
  display: inline-flex;
  align-items: center;
  gap: 0.45rem;
  padding: 0.55rem 1.1rem;
  border: 1px solid var(--gray-8);
  border-radius: 50px;
  font-family: 'Outfit', sans-serif;
  font-size: 0.82rem;
  font-weight: 500;
  color: var(--gray-11);
  text-decoration: none;
  transition: color 0.2s ease, border-color 0.2s ease;
}

.ps-cta-ghost:hover {
  color: var(--gray-12);
  border-color: rgba(255, 255, 255, 0.2);
}

.ps-cta-primary {
  position: relative;
  display: inline-flex;
  align-items: center;
  gap: 0.45rem;
  padding: 0.55rem 1.1rem;
  background: var(--green-9);
  color: #061208;
  font-family: 'Outfit', sans-serif;
  font-size: 0.82rem;
  font-weight: 700;
  border-radius: 50px;
  text-decoration: none;
  overflow: hidden;
  transition: transform 0.2s ease, box-shadow 0.2s ease;
}

.ps-cta-primary:hover {
  transform: translateY(-2px);
  box-shadow: 0 8px 24px rgba(0, 230, 118, 0.25);
}

/* ── Responsive ──────────────────────────────────────────── */
@media (max-width: 900px) {
  .ps-grid {
    grid-template-columns: 1fr;
    gap: 3rem;
  }

  .ps-sidebar {
    position: static;
    display: grid;
    grid-template-columns: 180px 1fr;
    gap: 1.5rem;
    align-items: start;
  }

  .ps-photo-wrap {
    margin-bottom: 0;
  }
}

@media (max-width: 560px) {
  .ps-sidebar {
    grid-template-columns: 1fr;
  }

  /* .ps-projects-grid {
    grid-template-columns: 1fr;
  } */

  .ps-cta-banner {
    flex-direction: column;
    align-items: flex-start;
  }
}
</style>