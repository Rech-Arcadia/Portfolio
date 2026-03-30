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

<template class="ft-footer">
  <section id="contact" class="contact-section section">
    <div class="container">

      <!-- ── Bloque hero del footer ─────────────────────────── -->
      <div class="ft-hero">
        <div class="ft-hero__left">
          <span class="ft-eyebrow">Disponible para proyectos</span>
          <h2 class="ft-cta-title">¿Tienes una <em>idea</em>?<br />Hagámosla realidad.</h2>
          <p class="ft-cta-sub">Desarrollo web · Diseño UI/UX · Consultoría frontend</p>
        </div>
        <div class="ft-hero__right">
          <a href="mailto:hola@ricardoarcadia.dev" class="ft-contact-btn">
            <span class="ft-contact-btn__text">Escribeme</span>
            <span class="ft-contact-btn__icon">
              <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" viewBox="0 0 24 24" fill="none"
                stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round">
                <path d="M7 17L17 7M17 7H7M17 7v10" />
              </svg>
            </span>
          </a>
          <div class="ft-social-row">
            <a v-for="s in socialLinks" :key="s.name" :href="s.url" :title="s.name" class="ft-social-btn"
              target="_blank" rel="noopener" v-html="s.icon" />
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Syne:wght@700;800&family=Outfit:wght@300;400;500;600&display=swap');

.exp-section {
  padding: 7rem 0;
}

/* ── Footer base ─────────────────────────────────────────── */
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

/* ── Hero del footer ─────────────────────────────────────── */
.ft-hero {
  display: flex;
  align-items: flex-end;
  justify-content: space-between;
  gap: 2rem;
  padding: 4rem 0 3.5rem;
  flex-wrap: wrap;
}

.ft-hero__left {
  display: flex;
  flex-direction: column;
  gap: 0.75rem;
}

.ft-eyebrow {
  font-family: 'Outfit', sans-serif;
  font-size: 0.7rem;
  font-weight: 500;
  letter-spacing: 0.18em;
  text-transform: uppercase;
  color: var(--green-9);
  display: flex;
  align-items: center;
  gap: 0.5rem;
}

.ft-eyebrow::before {
  content: '';
  display: inline-block;
  width: 20px;
  height: 1px;
  background: var(--green-9);
}

.ft-cta-title {
  font-family: 'Syne', sans-serif;
  font-size: clamp(2rem, 4.5vw, 3.4rem);
  font-weight: 800;
  letter-spacing: -0.04em;
  color: var(--gray-12);
  margin: 0;
  line-height: 1.1;
}

.ft-cta-title em {
  font-style: italic;
  color: var(--green-9);
}

.ft-cta-sub {
  font-family: 'Outfit', sans-serif;
  font-size: 0.85rem;
  color: var(--gray-9);
  font-weight: 300;
  margin: 0;
  letter-spacing: 0.02em;
}

.ft-hero__right {
  display: flex;
  flex-direction: column;
  align-items: flex-end;
  gap: 1.25rem;
  flex-shrink: 0;
}

/* Botón CTA */
.ft-contact-btn {
  display: inline-flex;
  align-items: center;
  gap: 0.6rem;
  padding: 0.75rem 1.5rem;
  background: var(--green-9);
  color: #061208;
  font-family: 'Outfit', sans-serif;
  font-size: 0.88rem;
  font-weight: 700;
  border-radius: 50px;
  text-decoration: none;
  transition: transform 0.2s cubic-bezier(0.34, 1.2, 0.64, 1), box-shadow 0.2s ease;
  white-space: nowrap;
}

.ft-contact-btn:hover {
  transform: translateY(-2px);
  box-shadow: 0 8px 28px rgba(0, 230, 118, 0.32);
}

.ft-contact-btn__icon {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 26px;
  height: 26px;
  background: rgba(0, 0, 0, 0.15);
  border-radius: 50%;
  flex-shrink: 0;
  transition: transform 0.2s ease;
}

.ft-contact-btn:hover .ft-contact-btn__icon {
  transform: translate(2px, -2px);
}

/* Social icons */
.ft-social-row {
  display: flex;
  gap: 0.5rem;
}

.ft-social-btn {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 36px;
  height: 36px;
  border-radius: 10px;
  border: 1px solid var(--gray-8);
  color: var(--gray-9);
  background: var(--gray-2);
  text-decoration: none;
  transition: color 0.2s ease, border-color 0.2s ease, background 0.2s ease, transform 0.2s ease;
}

.ft-social-btn:hover {
  color: var(--gray-12);
  border-color: var(--green-9);
  background: var(--green-3);
  transform: translateY(-2px);
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