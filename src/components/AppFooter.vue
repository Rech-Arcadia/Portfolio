<script setup>
import { footerLinks } from '../data/portfolioData.js';

const socialLinks = [
  {
    name: 'GitHub',
    url: '#',
    icon: `<svg viewBox="0 0 24 24" width="16" height="16" fill="currentColor"><path d="M12 2C6.477 2 2 6.484 2 12.017c0 4.425 2.865 8.18 6.839 9.504.5.092.682-.217.682-.483 0-.237-.008-.868-.013-1.703-2.782.605-3.369-1.343-3.369-1.343-.454-1.158-1.11-1.466-1.11-1.466-.908-.62.069-.608.069-.608 1.003.07 1.531 1.032 1.531 1.032.892 1.53 2.341 1.088 2.91.832.092-.647.35-1.088.636-1.338-2.22-.253-4.555-1.113-4.555-4.951 0-1.093.39-1.988 1.029-2.688-.103-.253-.446-1.272.098-2.65 0 0 .84-.27 2.75 1.026A9.564 9.564 0 0 1 12 6.844c.85.004 1.705.115 2.504.337 1.909-1.296 2.747-1.027 2.747-1.027.546 1.379.202 2.398.1 2.651.64.7 1.028 1.595 1.028 2.688 0 3.848-2.339 4.695-4.566 4.943.359.309.678.92.678 1.855 0 1.338-.012 2.419-.012 2.747 0 .268.18.58.688.482A10.019 10.019 0 0 0 22 12.017C22 6.484 17.522 2 12 2z"/></svg>`,
  },
  {
    name: 'LinkedIn',
    url: '#',
    icon: `<svg viewBox="0 0 24 24" width="16" height="16" fill="currentColor"><path d="M20.447 20.452h-3.554v-5.569c0-1.328-.027-3.037-1.852-3.037-1.853 0-2.136 1.445-2.136 2.939v5.667H9.351V9h3.414v1.561h.046c.477-.9 1.637-1.85 3.37-1.85 3.601 0 4.267 2.37 4.267 5.455v6.286zM5.337 7.433a2.062 2.062 0 0 1-2.063-2.065 2.064 2.064 0 1 1 2.063 2.065zm1.782 13.019H3.555V9h3.564v11.452zM22.225 0H1.771C.792 0 0 .774 0 1.729v20.542C0 23.227.792 24 1.771 24h20.451C23.2 24 24 23.227 24 22.271V1.729C24 .774 23.2 0 22.222 0h.003z"/></svg>`,
  },
  {
    name: 'X',
    url: '#',
    icon: `<svg viewBox="0 0 24 24" width="16" height="16" fill="currentColor"><path d="M18.244 2.25h3.308l-7.227 8.26 8.502 11.24H16.17l-4.714-6.231-5.401 6.231H2.744l7.737-8.835L1.254 2.25H8.08l4.261 5.634 5.903-5.634zm-1.161 17.52h1.833L7.084 4.126H5.117z"/></svg>`,
  },
  {
    name: 'YouTube',
    url: '#',
    icon: `<svg viewBox="0 0 24 24" width="16" height="16" fill="currentColor"><path d="M23.498 6.186a3.016 3.016 0 0 0-2.122-2.136C19.505 3.545 12 3.545 12 3.545s-7.505 0-9.377.505A3.017 3.017 0 0 0 .502 6.186C0 8.07 0 12 0 12s0 3.93.502 5.814a3.016 3.016 0 0 0 2.122 2.136c1.871.505 9.376.505 9.376.505s7.505 0 9.377-.505a3.015 3.015 0 0 0 2.122-2.136C24 15.93 24 12 24 12s0-3.93-.502-5.814zM9.545 15.568V8.432L15.818 12l-6.273 3.568z"/></svg>`,
  },
];

const currentYear = new Date().getFullYear();
</script>

<template>
  <footer class="ft-footer">

    <!-- ── Línea decorativa superior ─────────────────────── -->
    <div class="ft-top-bar" aria-hidden="true">
      <span class="ft-top-bar__line"></span>
      <span class="ft-top-bar__dot"></span>
      <span class="ft-top-bar__line"></span>
    </div>

    <div class="container">

      <!-- ── Divisor ─────────────────────────────────────────── -->
      <div class="ft-divider" aria-hidden="true"></div>

      <!-- ── Links grid ─────────────────────────────────────── -->
      <div class="ft-links-grid">

        <!-- Brand col -->
        <div class="ft-brand-col">
          <div class="ft-brand-logo">
            <span class="ft-brand-logo__icon">
              <svg xmlns="http://www.w3.org/2000/svg" width="14" height="14" viewBox="0 0 24 24" fill="none"
                stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round">
                <polyline points="16 18 22 12 16 6" />
                <polyline points="8 6 2 12 8 18" />
              </svg>
            </span>
            <span class="ft-brand-logo__name">Ricardo.dev</span>
          </div>
          <p class="ft-brand-desc">
            Frontend developer & UI designer basado en Guadalajara, MX.
            Construyendo interfaces que importan.
          </p>
          <span class="ft-badge">
            <span class="ft-badge__dot"></span>
            Abierto a trabajos
          </span>
        </div>

        <!-- Links cols -->
        <div v-for="(links, category) in footerLinks" :key="category" class="ft-link-col">
          <h4 class="ft-link-heading">{{ category }}</h4>
          <ul class="ft-link-list">
            <li v-for="link in links" :key="link">
              <a href="#" class="ft-link">
                {{ link }}
                <svg xmlns="http://www.w3.org/2000/svg" width="10" height="10" viewBox="0 0 24 24" fill="none"
                  stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"
                  class="ft-link__arrow">
                  <path d="M7 17L17 7M17 7H7M17 7v10" />
                </svg>
              </a>
            </li>
          </ul>
        </div>

      </div>

      <!-- ── Bottom bar ─────────────────────────────────────── -->
      <div class="ft-bottom">
        <span class="ft-copyright">
          © {{ currentYear }} Ricardo Arcadia Avalos — Hecho con Vue 3
        </span>
        <div class="ft-bottom__links">
          <a href="#" class="ft-bottom__link">Privacidad</a>
          <span class="ft-bottom__sep" aria-hidden="true">·</span>
          <a href="#" class="ft-bottom__link">Términos</a>
        </div>
      </div>

    </div>
  </footer>
</template>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Syne:wght@700;800&family=Outfit:wght@300;400;500;600&display=swap');

/* ── Footer base ─────────────────────────────────────────── */

.container {
  width: 90%;
  max-width: 1200px;
  margin: 0 auto;
  padding-top: 40px;
}

.ft-footer {
  background: var(--gray-1);
  padding-bottom: 2rem;
  position: relative;
  overflow: hidden;
}

/* Glow de fondo sutil */
.ft-footer::before {
  content: '';
  position: absolute;
  top: 0;
  left: 50%;
  transform: translateX(-50%);
  width: 600px;
  height: 300px;
  background: radial-gradient(ellipse at top, rgba(0, 230, 118, 0.06) 0%, transparent 70%);
  pointer-events: none;
}

/* ── Top bar decorativa ──────────────────────────────────── */
.ft-top-bar {
  display: flex;
  align-items: center;
  gap: 0;
  margin-bottom: 0;
}

.ft-top-bar__line {
  flex: 1;
  height: 1px;
  background: linear-gradient(90deg, transparent, var(--gray-8));
}

.ft-top-bar__line:last-child {
  background: linear-gradient(90deg, var(--gray-8), transparent);
}

.ft-top-bar__dot {
  width: 6px;
  height: 6px;
  border-radius: 50%;
  background: var(--green-9);
  flex-shrink: 0;
  box-shadow: 0 0 12px var(--green-9);
}


/* ── Links grid ──────────────────────────────────────────── */
.ft-links-grid {
  display: grid;
  grid-template-columns: 1.6fr repeat(4, 1fr);
  gap: 2rem 3rem;
  margin-bottom: 3rem;
  align-items: start;
}

/* Brand col */
.ft-brand-col {
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

.ft-brand-logo {
  display: inline-flex;
  align-items: center;
  gap: 0.5rem;
}

.ft-brand-logo__icon {
  width: 28px;
  height: 28px;
  border-radius: 8px;
  background: var(--green-2);
  border: 1px solid rgba(0, 230, 118, 0.2);
  color: var(--green-9);
  display: flex;
  align-items: center;
  justify-content: center;
  flex-shrink: 0;
}

.ft-brand-logo__name {
  font-family: 'Syne', sans-serif;
  font-size: 1rem;
  font-weight: 800;
  color: var(--gray-12);
  letter-spacing: -0.02em;
}

.ft-brand-desc {
  font-family: 'Outfit', sans-serif;
  font-size: 0.78rem;
  color: var(--gray-9);
  line-height: 1.65;
  font-weight: 300;
  margin: 0;
  max-width: 220px;
}

.ft-badge {
  display: inline-flex;
  align-items: center;
  gap: 0.4rem;
  padding: 0.25rem 0.7rem;
  background: var(--green-2);
  border: 1px solid rgba(0, 230, 118, 0.2);
  border-radius: 50px;
  font-family: 'Outfit', sans-serif;
  font-size: 0.65rem;
  font-weight: 600;
  color: var(--green-9);
  letter-spacing: 0.04em;
  width: fit-content;
}

.ft-badge__dot {
  width: 6px;
  height: 6px;
  border-radius: 50%;
  background: var(--green-9);
  animation: pulse-dot 2s ease-in-out infinite;
}

@keyframes pulse-dot {

  0%,
  100% {
    opacity: 1;
    transform: scale(1);
  }

  50% {
    opacity: 0.5;
    transform: scale(0.75);
  }
}

/* Link cols */
.ft-link-col {
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

.ft-link-heading {
  font-family: 'Syne', sans-serif;
  font-size: 0.78rem;
  font-weight: 700;
  color: var(--gray-12);
  margin: 0;
  text-transform: capitalize;
  letter-spacing: -0.01em;
}

.ft-link-list {
  display: flex;
  flex-direction: column;
  gap: 0.6rem;
  list-style: none;
  padding: 0;
  margin: 0;
}

.ft-link {
  font-family: 'Outfit', sans-serif;
  font-size: 0.78rem;
  font-weight: 400;
  color: var(--gray-9);
  text-decoration: none;
  display: inline-flex;
  align-items: center;
  gap: 0.3rem;
  transition: color 0.2s ease;
}

.ft-link__arrow {
  opacity: 0;
  transform: translate(-2px, 2px);
  transition: opacity 0.2s ease, transform 0.2s ease;
  flex-shrink: 0;
}

.ft-link:hover {
  color: var(--gray-12);
}

.ft-link:hover .ft-link__arrow {
  opacity: 1;
  transform: translate(0, 0);
}

/* ── Bottom bar ──────────────────────────────────────────── */
.ft-bottom {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding-top: 2rem;
  border-top: 1px solid var(--gray-8);
  flex-wrap: wrap;
  gap: 0.75rem;
  opacity: 0.6;
}

.ft-copyright {
  font-family: 'Outfit', sans-serif;
  font-size: 0.72rem;
  color: var(--gray-9);
  font-weight: 400;
}

.ft-bottom__links {
  display: flex;
  align-items: center;
  gap: 0.6rem;
}

.ft-bottom__link {
  font-family: 'Outfit', sans-serif;
  font-size: 0.72rem;
  color: var(--gray-9);
  text-decoration: none;
  transition: color 0.2s ease;
}

.ft-bottom__link:hover {
  color: var(--gray-12);
}

.ft-bottom__sep {
  color: var(--gray-8);
  font-size: 0.7rem;
}

/* ── Responsive ──────────────────────────────────────────── */
@media (max-width: 1024px) {
  .ft-links-grid {
    grid-template-columns: 1fr repeat(2, 1fr);
    gap: 2rem;
  }

  .ft-brand-col {
    grid-column: 1 / -1;
    flex-direction: row;
    align-items: flex-start;
    flex-wrap: wrap;
    gap: 1.5rem;
  }

  .ft-brand-desc {
    max-width: 300px;
  }
}

@media (max-width: 768px) {
  .ft-hero {
    flex-direction: column;
    align-items: flex-start;
    gap: 2rem;
    padding: 3rem 0 2.5rem;
  }

  .ft-hero__right {
    align-items: flex-start;
    flex-direction: row;
    flex-wrap: wrap;
    gap: 1rem;
  }

  .ft-links-grid {
    grid-template-columns: repeat(2, 1fr);
    gap: 2rem 1.5rem;
  }

  .ft-brand-col {
    grid-column: 1 / -1;
    flex-direction: column;
    gap: 0.75rem;
  }
}

@media (max-width: 560px) {
  .ft-cta-title {
    font-size: clamp(1.7rem, 8vw, 2.2rem);
  }

  .ft-links-grid {
    grid-template-columns: repeat(2, 1fr);
    gap: 1.5rem 1rem;
  }

  .ft-bottom {
    flex-direction: column;
    align-items: flex-start;
    gap: 0.5rem;
  }
}
</style>