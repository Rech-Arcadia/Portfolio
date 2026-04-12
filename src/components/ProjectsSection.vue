<script setup>
import deusarcImg from '@/assets/images/projects/figma/DeusArc-UI.png'
import rosysImg from '@/assets/images/projects/figma/RosysCake-UI.png'
import rosysMobileImg from '@/assets/images/projects/figma/Mobile-RosysCake-UI.png'
import dulcesSueñosImg from '@/assets/images/projects/develop/DulcesSueños-Web.png'
import nutriVidaImg from '@/assets/images/projects/develop/NutriVida-Web.png'

const devProjects = [
    {
        id: 1,
        title: 'NutriVida',
        description: 'LandingPage para nutricionista profesional, moderna, con responsive design y animaciones',
        image: nutriVidaImg,
        tags: ['Vue 3', 'Pinia', 'TypeScript', 'GSAP'],
        liveUrl: 'https://nutricion-page.vercel.app/',
        githubUrl: 'https://github.com/Rech-Arcadia/nutricion',
        year: '2026',
    },
    {
        id: 2,
        title: 'Landing Page - Dulces Sueños',
        description: 'Landing page para campaña artesanal, con diseño responsivo, animaciones sutiles.',
        image: dulcesSueñosImg,
        tags: ['HTML', 'CSS', 'JavaScript'],
        liveUrl: 'https://rech-arcadia.github.io/',
        githubUrl: 'https://github.com/Rech-Arcadia/Rech-Arcadia.github.io',
        year: '2021',
    },
    // {
    //     id: 3,
    //     title: 'App Gestión de Tareas',
    //     description: 'Herramienta colaborativa estilo Kanban con tiempo real vía WebSockets y notificaciones push.',
    //     image: 'https://images.unsplash.com/photo-1611224923853-80b023f02d71?q=80&w=800&auto=format&fit=crop',
    //     tags: ['Vue 3', 'Vite', 'Tailwind', 'Socket.io'],
    //     liveUrl: '#',
    //     githubUrl: '#',
    //     year: '2023',
    // },
    // {
    //     id: 4,
    //     title: 'Blog Técnico',
    //     description: 'Blog estático generado con Nuxt Content, SEO optimizado y soporte para MDX.',
    //     image: 'https://images.unsplash.com/photo-1486312338219-ce68d2c6f44d?q=80&w=800&auto=format&fit=crop',
    //     tags: ['Nuxt 3', 'Nuxt Content', 'Tailwind'],
    //     liveUrl: '#',
    //     githubUrl: '#',
    //     year: '2023',
    // },
]

const designProjects = [
    {
        id: 5,
        title: 'DeusArc Web UI',
        description: 'Sistema de diseño de DeusArc para app de merch: componentes, tokens de color y flujos de usuario.',
        image: deusarcImg,
        tags: ['Figma', 'Design System', 'Dark Mode'],
        liveUrl: 'https://www.figma.com/proto/Ep4OXhu9z0dwXHC5oo7bYj/DeusArc?node-id=197-3&t=89fjgv421irXxjmd-1',
        year: '2025',
    },
    {
        id: 6,
        title: 'Rosys Cake UI',
        description: 'Diseño de Ecommerce de pastelería: interfaz visual, experiencia de usuario y prototipo interactivo.',
        image: rosysImg,
        tags: ['Figma', 'Design System', 'Dark Mode'],
        liveUrl: 'https://www.figma.com/proto/aRXZrmP2qCHjmoHd4UAUWr/Rosy-s-Cake?node-id=1-2&p=f&t=aigmBtMm6qYZIaaw-1&scaling=min-zoom&content-scaling=fixed&page-id=0%3A1',
        year: '2026',
    },
    {
        id: 7,
        title: 'Mobile App - Rosys Cake',
        description: 'Diseño UX/UI de app móvil para Rosys Cake: onboarding, catálogo de productos y proceso de compra.',
        image: rosysMobileImg,
        tags: ['Figma', 'Mobile UI', 'Prototype', 'UX'],
        liveUrl: 'https://www.figma.com/proto/w8bGPypkegjWEZzIZrkH25/Untitled?node-id=5-6&starting-point-node-id=5%3A6&t=F2HPXavj6ub0ryjX-1',
        year: '2025',
    },
    // {
    //     id: 8,
    //     title: 'Mobile App — Health',
    //     description: 'Diseño UX/UI de app móvil: onboarding, dashboard y flujos de seguimiento de salud.',
    //     image: 'https://images.unsplash.com/photo-1576091160399-112ba8d25d1d?q=80&w=800&auto=format&fit=crop',
    //     tags: ['Figma', 'Mobile UI', 'Prototype', 'UX'],
    //     liveUrl: '#',
    //     year: '2023',
    // },
]
</script>

<template>
    <section id="projects" class="pj-section section">
        <div class="container">

            <!-- ── Page header ──────────────────────────────── -->
            <div class="pj-page-header">
                <span class="pj-eyebrow">Portafolio</span>
                <h2 class="pj-page-title">Trabajo realizado</h2>
                <p class="pj-page-sub">Desarrollo web y diseño de interfaces — proyectos reales, resultados reales.</p>
            </div>

            <!-- ── Dos columnas ─────────────────────────────── -->
            <div class="pj-columns">

                <!-- Columna Desarrollo -->
                <div class="pj-col">
                    <div class="pj-col-header">
                        <div class="pj-col-label">
                            <span class="pj-col-icon pj-col-icon--dev">
                                <svg xmlns="http://www.w3.org/2000/svg" width="14" height="14" viewBox="0 0 24 24"
                                    fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round"
                                    stroke-linejoin="round">
                                    <polyline points="16 18 22 12 16 6" />
                                    <polyline points="8 6 2 12 8 18" />
                                </svg>
                            </span>
                            <span class="pj-col-name">Desarrollo Web</span>
                        </div>
                        <span class="pj-col-count">{{ devProjects.length }} proyectos</span>
                    </div>

                    <div class="pj-list">
                        <a v-for="(p, i) in devProjects" :key="p.id" :href="p.liveUrl" target="_blank"
                            rel="noopener noreferrer" class="pj-card" :style="{ animationDelay: (i * 0.07) + 's' }">
                            <!-- Imagen -->
                            <div class="pj-img-wrap">
                                <img :src="p.image" :alt="p.title" class="pj-img" loading="lazy" />
                                <span class="pj-year">{{ p.year }}</span>
                                <div class="pj-img-shine" aria-hidden="true"></div>
                            </div>

                            <!-- Cuerpo -->
                            <div class="pj-body">
                                <div class="pj-body-top">
                                    <h3 class="pj-title">{{ p.title }}</h3>
                                    <!-- Botones -->
                                    <div class="pj-btns" @click.stop>
                                        <a :href="p.liveUrl" target="_blank" rel="noopener" class="pj-btn-live"
                                            title="Ver proyecto">
                                            <svg xmlns="http://www.w3.org/2000/svg" width="12" height="12"
                                                viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5"
                                                stroke-linecap="round" stroke-linejoin="round">
                                                <path d="M18 13v6a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2V8a2 2 0 0 1 2-2h6" />
                                                <polyline points="15 3 21 3 21 9" />
                                                <line x1="10" y1="14" x2="21" y2="3" />
                                            </svg>
                                            Live
                                        </a>
                                        <a v-if="p.githubUrl" :href="p.githubUrl" target="_blank" rel="noopener"
                                            class="pj-btn-gh" title="Ver en GitHub" @click.stop>
                                            <svg viewBox="0 0 24 24" width="13" height="13" fill="currentColor">
                                                <path
                                                    d="M12 2C6.477 2 2 6.484 2 12.017c0 4.425 2.865 8.18 6.839 9.504.5.092.682-.217.682-.483 0-.237-.008-.868-.013-1.703-2.782.605-3.369-1.343-3.369-1.343-.454-1.158-1.11-1.466-1.11-1.466-.908-.62.069-.608.069-.608 1.003.07 1.531 1.032 1.531 1.032.892 1.53 2.341 1.088 2.91.832.092-.647.35-1.088.636-1.338-2.22-.253-4.555-1.113-4.555-4.951 0-1.093.39-1.988 1.029-2.688-.103-.253-.446-1.272.098-2.65 0 0 .84-.27 2.75 1.026A9.564 9.564 0 0 1 12 6.844c.85.004 1.705.115 2.504.337 1.909-1.296 2.747-1.027 2.747-1.027.546 1.379.202 2.398.1 2.651.64.7 1.028 1.595 1.028 2.688 0 3.848-2.339 4.695-4.566 4.943.359.309.678.92.678 1.855 0 1.338-.012 2.419-.012 2.747 0 .268.18.58.688.482A10.019 10.019 0 0 0 22 12.017C22 6.484 17.522 2 12 2z" />
                                            </svg>
                                            GitHub
                                        </a>
                                    </div>
                                </div>

                                <p class="pj-desc">{{ p.description }}</p>

                                <div class="pj-tags">
                                    <span v-for="tag in p.tags" :key="tag" class="pj-tag pj-tag--dev">{{ tag }}</span>
                                </div>
                            </div>

                            <!-- Flecha hover -->
                            <span class="pj-arrow" aria-hidden="true">
                                <svg xmlns="http://www.w3.org/2000/svg" width="15" height="15" viewBox="0 0 24 24"
                                    fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round"
                                    stroke-linejoin="round">
                                    <path d="M7 17L17 7M17 7H7M17 7v10" />
                                </svg>
                            </span>
                        </a>
                    </div>
                </div>

                <!-- Divisor vertical -->
                <div class="pj-vdivider" aria-hidden="true"></div>

                <!-- Columna Diseño -->
                <div class="pj-col">
                    <div class="pj-col-header">
                        <div class="pj-col-label">
                            <span class="pj-col-icon pj-col-icon--figma">
                                <svg viewBox="0 0 24 24" width="14" height="14" fill="currentColor">
                                    <path
                                        d="M5 5.5A3.5 3.5 0 0 1 8.5 2H12v7H8.5A3.5 3.5 0 0 1 5 5.5zM12 2h3.5a3.5 3.5 0 1 1 0 7H12V2zM12 12.5a3.5 3.5 0 1 1 7 0 3.5 3.5 0 0 1-7 0zM5 19.5A3.5 3.5 0 0 1 8.5 16H12v3.5a3.5 3.5 0 1 1-7 0zM5 12.5A3.5 3.5 0 0 1 8.5 9H12v7H8.5A3.5 3.5 0 0 1 5 12.5z" />
                                </svg>
                            </span>
                            <span class="pj-col-name">Diseño Figma</span>
                        </div>
                        <span class="pj-col-count">{{ designProjects.length }} proyectos</span>
                    </div>

                    <div class="pj-list">
                        <a v-for="(p, i) in designProjects" :key="p.id" :href="p.liveUrl" target="_blank"
                            rel="noopener noreferrer" class="pj-card"
                            :style="{ animationDelay: (i * 0.07 + 0.12) + 's' }">
                            <div class="pj-img-wrap">
                                <img :src="p.image" :alt="p.title" class="pj-img" loading="lazy" />
                                <span class="pj-year">{{ p.year }}</span>
                                <div class="pj-img-shine" aria-hidden="true"></div>
                            </div>

                            <div class="pj-body">
                                <div class="pj-body-top">
                                    <h3 class="pj-title">{{ p.title }}</h3>
                                    <div class="pj-btns">
                                        <a :href="p.liveUrl" target="_blank" rel="noopener"
                                            class="pj-btn-live pj-btn-live--figma" title="Abrir en Figma" @click.stop>
                                            <svg viewBox="0 0 24 24" width="12" height="12" fill="currentColor">
                                                <path
                                                    d="M5 5.5A3.5 3.5 0 0 1 8.5 2H12v7H8.5A3.5 3.5 0 0 1 5 5.5zM12 2h3.5a3.5 3.5 0 1 1 0 7H12V2zM12 12.5a3.5 3.5 0 1 1 7 0 3.5 3.5 0 0 1-7 0zM5 19.5A3.5 3.5 0 0 1 8.5 16H12v3.5a3.5 3.5 0 1 1-7 0zM5 12.5A3.5 3.5 0 0 1 8.5 9H12v7H8.5A3.5 3.5 0 0 1 5 12.5z" />
                                            </svg>
                                            Figma
                                        </a>
                                    </div>
                                </div>

                                <p class="pj-desc">{{ p.description }}</p>

                                <div class="pj-tags">
                                    <span v-for="tag in p.tags" :key="tag" class="pj-tag pj-tag--figma">{{ tag }}</span>
                                </div>
                            </div>

                            <span class="pj-arrow" aria-hidden="true">
                                <svg xmlns="http://www.w3.org/2000/svg" width="15" height="15" viewBox="0 0 24 24"
                                    fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round"
                                    stroke-linejoin="round">
                                    <path d="M7 17L17 7M17 7H7M17 7v10" />
                                </svg>
                            </span>
                        </a>
                    </div>
                </div>

            </div>
        </div>
    </section>
</template>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Syne:wght@700;800&family=Outfit:wght@300;400;500;600&display=swap');

/* ── Page header ─────────────────────────────────────────── */
.pj-page-header {
    display: flex;
    flex-direction: column;
    align-items: center;
    text-align: center;
    gap: 0.5rem;
    margin-bottom: 4rem;
}

.pj-eyebrow {
    font-family: 'Outfit', sans-serif;
    font-size: 0.72rem;
    font-weight: 500;
    letter-spacing: 0.18em;
    text-transform: uppercase;
    color: var(--green-9);
}

.pj-page-title {
    font-family: 'Syne', sans-serif;
    font-size: clamp(2rem, 4vw, 3rem);
    font-weight: 800;
    letter-spacing: -0.03em;
    color: var(--gray-12);
    margin: 0;
}

.pj-page-sub {
    font-family: 'Outfit', sans-serif;
    font-size: 0.975rem;
    color: var(--gray-11);
    font-weight: 300;
    margin: 0;
    max-width: 520px;
    line-height: 1.7;
}

/* ── Layout de dos columnas ──────────────────────────────── */
.pj-columns {
    display: grid;
    grid-template-columns: 1fr 1px 1fr;
    gap: 0 3.5rem;
    align-items: start;
    display: flex;
    flex-direction: row;
    gap: 2rem 3.5rem;
}

.pj-vdivider {
    background: var(--gray-8);
    height: 100%;
    /* min-height: 400px; */
    opacity: 0.5;
}

/* ── Encabezado de columna ───────────────────────────────── */
.pj-col-header {
    display: flex;
    align-items: center;
    justify-content: space-between;
    margin-bottom: 1.5rem;
    padding-bottom: 1rem;
    border-bottom: 1px solid var(--gray-8);
}

.pj-col-label {
    display: flex;
    align-items: center;
    gap: 0.6rem;
}

.pj-col-icon {
    width: 30px;
    height: 30px;
    border-radius: 8px;
    display: flex;
    align-items: center;
    justify-content: center;
    flex-shrink: 0;
}

.pj-col-icon--dev {
    background: var(--green-2);
    border: 1px solid rgba(0, 230, 118, 0.2);
    color: var(--green-9);
}

.pj-col-icon--figma {
    background: var(--figma-bg);
    border: 1px solid var(--figma-border);
    color: var(--figma-color);
}

.pj-col-name {
    font-family: 'Syne', sans-serif;
    font-size: 1.05rem;
    font-weight: 700;
    color: var(--gray-12);
    letter-spacing: -0.01em;
}

.pj-col-count {
    font-family: 'Outfit', sans-serif;
    font-size: 0.7rem;
    font-weight: 500;
    color: var(--gray-11);
    letter-spacing: 0.04em;
}

/* ── Lista de cards ──────────────────────────────────────── */
.pj-list {
    display: flex;
    flex-direction: column;
    gap: 1rem;
}

/* ── Card ────────────────────────────────────────────────── */
.pj-card {
    display: grid;
    grid-template-columns: 120px 1fr auto;
    gap: 1rem;
    align-items: start;
    padding: 1rem;
    background: var(--gray-2);
    border: 1px solid var(--gray-8);
    border-radius: 14px;
    text-decoration: none;
    color: inherit;
    position: relative;
    overflow: hidden;
    transition:
        background 0.25s ease,
        border-color 0.25s ease,
        transform 0.25s cubic-bezier(0.34, 1.2, 0.64, 1),
        box-shadow 0.25s ease;
    animation: card-in 0.45s ease both;
}

@keyframes card-in {
    from {
        opacity: 0;
        transform: translateY(14px);
    }

    to {
        opacity: 1;
        transform: translateY(0);
    }
}

.pj-card:hover {
    /* background: var(--bg-card-hover); */
    background: var(--gray-3);
    border-color: rgba(255, 255, 255, 0.11);
    transform: translateX(4px);
    box-shadow: 0 8px 32px rgba(0, 0, 0, 0.3);
}

/* ── Imagen ──────────────────────────────────────────────── */
.pj-img-wrap {
    position: relative;
    border-radius: 8px;
    overflow: hidden;
    aspect-ratio: 6 / 5;
    flex-shrink: 0;
}

.pj-img {
    width: 100%;
    height: 100%;
    object-fit: cover;
    display: block;
    transition: transform 0.4s ease;
}

.pj-card:hover .pj-img {
    transform: scale(1.07);
}

/* Brillo que barre en hover */
.pj-img-shine {
    position: absolute;
    inset: 0;
    background: linear-gradient(105deg, transparent 40%, rgba(255, 255, 255, 0.12) 50%, transparent 60%);
    background-size: 200% 100%;
    background-position: 200% 0;
    transition: background-position 0.5s ease;
}

.pj-card:hover .pj-img-shine {
    background-position: -60% 0;
}

.pj-year {
    position: absolute;
    bottom: 6px;
    left: 6px;
    font-family: 'Outfit', sans-serif;
    font-size: 0.58rem;
    font-weight: 600;
    letter-spacing: 0.08em;
    color: rgba(255, 255, 255, 0.8);
    background: rgba(0, 0, 0, 0.55);
    backdrop-filter: blur(6px);
    border-radius: 50px;
    padding: 0.15rem 0.45rem;
}

/* ── Cuerpo ──────────────────────────────────────────────── */
.pj-body {
    display: flex;
    flex-direction: column;
    gap: 0.4rem;
    min-width: 0;
}

.pj-body-top {
    display: flex;
    align-items: flex-start;
    justify-content: space-between;
    gap: 0.5rem;
}

.pj-title {
    font-family: 'Syne', sans-serif;
    font-size: 0.9rem;
    font-weight: 700;
    color: var(--gray-12);
    margin: 0;
    line-height: 1.3;
    letter-spacing: -0.01em;
}

.pj-desc {
    font-family: 'Outfit', sans-serif;
    font-size: 0.76rem;
    color: var(--gray-11);
    line-height: 1.6;
    margin: 0;
    /* Limitar a 2 líneas */
    display: -webkit-box;
    -webkit-line-clamp: 2;
    -webkit-box-orient: vertical;
    overflow: hidden;
}

/* ── Tags ────────────────────────────────────────────────── */
.pj-tags {
    display: flex;
    flex-wrap: wrap;
    gap: 0.3rem;
    margin-top: 0.15rem;
}

.pj-tag {
    font-family: 'Outfit', sans-serif;
    font-size: 0.58rem;
    font-weight: 500;
    border-radius: 50px;
    padding: 0.15rem 0.5rem;
    letter-spacing: 0.04em;
    white-space: nowrap;
}

.pj-tag--dev {
    color: var(--green-9);
    background: var(--green-2);
    border: 1px solid rgba(0, 230, 118, 0.15);
}

.pj-tag--figma {
    color: #a259ff;
    background: rgba(162, 89, 255, 0.08);
    border: 1px solid rgba(162, 89, 255, 0.2);
}

/* ── Botones dentro de card ──────────────────────────────── */
.pj-btns {
    display: flex;
    gap: 0.35rem;
    flex-shrink: 0;
}

.pj-btn-live {
    display: inline-flex;
    align-items: center;
    gap: 0.3rem;
    padding: 0.28rem 0.65rem;
    background: var(--green-9);
    color: #061208;
    font-family: 'Outfit', sans-serif;
    font-size: 0.65rem;
    font-weight: 700;
    border-radius: 50px;
    text-decoration: none;
    white-space: nowrap;
    transition: transform 0.2s ease, box-shadow 0.2s ease;
}

.pj-btn-live:hover {
    transform: translateY(-1px);
    box-shadow: 0 4px 14px rgba(0, 230, 118, 0.28);
}

.pj-btn-live--figma {
    background: #773ac7;
    color: #fff;
}

.pj-btn-live--figma:hover {
    box-shadow: 0 4px 14px rgba(162, 89, 255, 0.3);
}

.pj-btn-gh {
    display: inline-flex;
    align-items: center;
    gap: 0.3rem;
    padding: 0.28rem 0.6rem;
    border: 1px solid var(--gray-8);
    border-radius: 50px;
    font-family: 'Outfit', sans-serif;
    font-size: 0.65rem;
    font-weight: 500;
    color: var(--gray-11);
    text-decoration: none;
    white-space: nowrap;
    transition: color 0.2s ease, border-color 0.2s ease;
}

.pj-btn-gh:hover {
    color: var(--gray-12);
    border-color: rgba(255, 255, 255, 0.22);
}

/* ── Flecha hover ────────────────────────────────────────── */
.pj-arrow {
    display: flex;
    align-items: center;
    justify-content: center;
    color: var(--gray-11);
    flex-shrink: 0;
    opacity: 0;
    transform: translateX(-4px);
    transition: opacity 0.25s ease, transform 0.25s ease, color 0.25s ease;
    align-self: center;
}

.pj-card:hover .pj-arrow {
    opacity: 1;
    transform: translateX(0);
    color: var(--gray-12);
}

/* ── Responsive ──────────────────────────────────────────── */
@media (max-width: 1024px) {
    .pj-columns {
        flex-direction: column;
        gap: 3.5rem;
    }

    .pj-vdivider {
        display: none;
    }

    .pj-col {
        width: 100%;
    }

    /* Grid de 2 cards por fila */
    .pj-list {
        display: grid;
        grid-template-columns: repeat(2, 1fr);
        gap: 1rem;
    }

    /* Card vertical dentro del grid */
    .pj-list .pj-card {
        grid-template-columns: 1fr;
        grid-template-rows: auto 1fr;
        gap: 0.75rem;
    }

    .pj-list .pj-card .pj-img-wrap {
        aspect-ratio: 16 / 7;
        width: 100%;
    }

    .pj-list .pj-card .pj-arrow {
        display: none;
    }
}

@media (max-width: 768px) {

    /* 1 card por fila, horizontal (imagen + contenido) */
    .pj-list {
        display: flex;
        flex-direction: column;
        gap: 1rem;
    }

    .pj-card {
        grid-template-columns: 100px 1fr auto;
        gap: 0.85rem;
        padding: 0.9rem;
    }

    .pj-img-wrap {
        aspect-ratio: 4 / 3;
    }

    .pj-title {
        font-size: 0.85rem;
    }

    .pj-desc {
        font-size: 0.74rem;
        -webkit-line-clamp: 2;
    }

    .pj-btn-live,
    .pj-btn-gh {
        padding: 0.3rem 0.6rem;
        font-size: 0.64rem;
    }

    .pj-tag {
        font-size: 0.58rem;
    }

    .pj-page-title {
        font-size: clamp(1.7rem, 6vw, 2.4rem);
    }
}

@media (max-width: 560px) {

    /* Columns stacked */
    .pj-columns {
        flex-direction: column;
        gap: 3rem;
    }

    .pj-vdivider {
        display: none;
    }

    /* Card vertical */
    .pj-card {
        grid-template-columns: 1fr;
        grid-template-rows: auto 1fr;
        gap: 0.75rem;
        padding: 0.85rem;
    }

    /* Imagen full-width con aspect-ratio horizontal */
    .pj-img-wrap {
        aspect-ratio: 16 / 7;
        border-radius: 8px;
        width: 100%;
    }

    /* Ocultar flecha (no hay hover en touch) */
    .pj-arrow {
        display: none;
    }

    /* Body legible */
    .pj-body {
        gap: 0.5rem;
    }

    .pj-body-top {
        flex-direction: row;
        align-items: flex-start;
        gap: 0.5rem;
    }

    .pj-title {
        font-size: 0.85rem;
    }

    .pj-desc {
        font-size: 0.74rem;
        -webkit-line-clamp: 3;
    }

    /* Botones más fáciles de tocar */
    .pj-btn-live,
    .pj-btn-gh {
        padding: 0.35rem 0.75rem;
        font-size: 0.68rem;
    }

    /* Tags */
    .pj-tag {
        font-size: 0.6rem;
    }

    /* Page header */
    .pj-page-title {
        font-size: clamp(1.6rem, 7vw, 2.2rem);
    }

    .pj-page-sub {
        font-size: 0.88rem;
    }

    /* Col header */
    .pj-col-header {
        margin-bottom: 1rem;
    }
}
</style>