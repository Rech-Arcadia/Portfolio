<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

const experiences = [
    {
        id: 1,
        role: 'Junior Web Developer',
        company: 'Componentes y Tecnología de México - DDTech',
        period: 'Agosto 2025 — Presente',
        duration: '8 meses',
        type: 'Tiempo completo',
        location: 'Zapopan, Jalisco',
        description: 'Me encargo del Design System, optimizando su rendimiento y definiendo la arquitectura frontend, mientras desarrollo aplicaciones web modernas en colaboración con equipos en proyectos innovadores.',
        achievements: ['Implementación de design system propio', 'Optimización de performance y mejores prácticas en frontend', 'Reducción del 60% en tiempo de carga'],
        tags: ['Vue 3', 'Figma', 'Pinia', 'Vite'],
        current: true,
    },
    {
        id: 2,
        role: 'Técnico en equipo de cómputo',
        company: 'Computación para el diseño',
        period: 'Feb 2021 — Ago 2021',
        duration: '6 meses',
        type: 'Tiempo completo',
        location: 'Puerto Vallarta, Jalisco',
        description: 'Mi rol era cotizar equipos de cómputo para posteriormente comenzar con el armado e instalación de estos dependiendo de las necesidades del cliente.',
        achievements: ['Asesoría técnica y cotización', 'Armado e instalación de equipos', 'Optimización de recursos y tiempos de entrega'],
        tags: ['Soporte TI', 'Atención a clientes', 'Hardware'],
        current: false,
    }
]

// IntersectionObserver para animar cada item al entrar en viewport
const itemRefs = ref([])
const visibleItems = ref(new Set())
const lineVisible = ref(false)

let observer = null

onMounted(() => {
    observer = new IntersectionObserver(
        (entries) => {
            entries.forEach((entry) => {
                if (entry.isIntersecting) {
                    const id = Number(entry.target.dataset.id)
                    if (id === 0) {
                        lineVisible.value = true
                    } else {
                        visibleItems.value = new Set([...visibleItems.value, id])
                    }
                }
            })
        },
        { threshold: 0.15 }
    )

    // Observar la línea
    const lineEl = document.querySelector('.exp-line-trigger')
    if (lineEl) observer.observe(lineEl)

    // Observar cada item
    itemRefs.value.forEach((el) => {
        if (el) observer.observe(el)
    })
})

onUnmounted(() => {
    if (observer) observer.disconnect()
})
</script>

<template>
    <section id="experience" class="exp-section section">
        <div class="container">

            <!-- Header -->
            <div class="exp-header">
                <span class="exp-eyebrow">Trayectoria</span>
                <h2 class="exp-title">Experiencia Laboral</h2>
                <p class="exp-sub">Años construyendo productos digitales que funcionan.</p>
            </div>

            <!-- Timeline -->
            <div class="exp-timeline">

                <!-- Línea vertical -->
                <div class="exp-line-trigger" data-id="0" aria-hidden="true">
                    <div class="exp-line" :class="{ 'exp-line--visible': lineVisible }"></div>
                </div>

                <!-- Items -->
                <div v-for="(exp, i) in experiences" :key="exp.id" class="exp-item"
                    :class="{ 'exp-item--visible': visibleItems.has(exp.id) }" :data-id="exp.id"
                    :ref="el => itemRefs[i] = el" :style="{ transitionDelay: (i * 0.08) + 's' }">

                    <!-- Nodo en la línea -->
                    <div class="exp-node" :class="{ 'exp-node--active': exp.current }">
                        <span class="exp-node-dot"></span>
                        <span v-if="exp.current" class="exp-node-pulse"></span>
                    </div>

                    <!-- Card -->
                    <article class="exp-card" :class="{ 'exp-card--current': exp.current }">

                        <!-- Borde izquierdo glow (solo item actual) -->
                        <div v-if="exp.current" class="exp-card-glow" aria-hidden="true"></div>

                        <!-- Top row -->
                        <div class="exp-card-top">
                            <div class="exp-card-meta">
                                <span class="exp-period">{{ exp.period }}</span>
                                <span class="exp-duration">· {{ exp.duration }}</span>
                            </div>
                            <div class="exp-badges">
                                <span class="exp-badge exp-badge--type">{{ exp.type }}</span>
                                <span v-if="exp.current" class="exp-badge exp-badge--current">
                                    <span class="exp-badge-dot"></span>
                                    Actual
                                </span>
                            </div>
                        </div>

                        <!-- Role + company -->
                        <div class="exp-card-heading">
                            <h3 class="exp-role">{{ exp.role }}</h3>
                            <div class="exp-company-row">
                                <svg class="exp-company-icon" xmlns="http://www.w3.org/2000/svg" width="13" height="13"
                                    viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"
                                    stroke-linecap="round" stroke-linejoin="round">
                                    <path d="M3 9l9-7 9 7v11a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2z" />
                                    <polyline points="9 22 9 12 15 12 15 22" />
                                </svg>
                                <span class="exp-company">{{ exp.company }}</span>
                                <span class="exp-separator" aria-hidden="true">·</span>
                                <svg class="exp-company-icon" xmlns="http://www.w3.org/2000/svg" width="13" height="13"
                                    viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"
                                    stroke-linecap="round" stroke-linejoin="round">
                                    <path d="M21 10c0 7-9 13-9 13s-9-6-9-13a9 9 0 0 1 18 0z" />
                                    <circle cx="12" cy="10" r="3" />
                                </svg>
                                <span class="exp-location">{{ exp.location }}</span>
                            </div>
                        </div>

                        <!-- Descripción -->
                        <p class="exp-desc">{{ exp.description }}</p>

                        <!-- Logros -->
                        <ul class="exp-achievements">
                            <li v-for="a in exp.achievements" :key="a" class="exp-achievement">
                                <svg xmlns="http://www.w3.org/2000/svg" width="11" height="11" viewBox="0 0 24 24"
                                    fill="none" stroke="currentColor" stroke-width="3" stroke-linecap="round"
                                    stroke-linejoin="round" aria-hidden="true">
                                    <polyline points="20 6 9 17 4 12" />
                                </svg>
                                {{ a }}
                            </li>
                        </ul>

                        <!-- Tags -->
                        <div class="exp-tags">
                            <span v-for="tag in exp.tags" :key="tag" class="exp-tag">{{ tag }}</span>
                        </div>

                    </article>
                </div>

            </div>
        </div>
    </section>
</template>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Syne:wght@700;800&family=Outfit:wght@300;400;500;600&display=swap');

/* ── Section ─────────────────────────────────────────────── */
.exp-section {
    padding: 7rem 0;
}

/* ── Header ──────────────────────────────────────────────── */
.exp-header {
    display: flex;
    flex-direction: column;
    align-items: center;
    text-align: center;
    gap: 0.5rem;
    margin-bottom: 4.5rem;
}

.exp-eyebrow {
    font-family: 'Outfit', sans-serif;
    font-size: 0.72rem;
    font-weight: 500;
    letter-spacing: 0.18em;
    text-transform: uppercase;
    color: var(--green-9);
}

.exp-title {
    font-family: 'Syne', sans-serif;
    font-size: clamp(2rem, 4vw, 3rem);
    font-weight: 800;
    letter-spacing: -0.03em;
    color: var(--gray-12);
    margin: 0;
}

.exp-sub {
    font-family: 'Outfit', sans-serif;
    font-size: 0.975rem;
    color: var(--gray-11);
    font-weight: 300;
    margin: 0;
}

/* ── Timeline container ──────────────────────────────────── */
.exp-timeline {
    position: relative;
    max-width: 720px;
    margin: 0 auto;
    padding-left: 34px;
}

/* ── Línea vertical ──────────────────────────────────────── */
.exp-line-trigger {
    position: absolute;
    left: 11px;
    top: 24px;
    bottom: 0;
    width: 2px;
}

.exp-line {
    width: 100%;
    height: 0%;
    background: linear-gradient(to bottom,
            var(--green-9) 0%,
            rgba(0, 230, 118, 0.3) 60%,
            transparent 100%);
    border-radius: 99px;
    transition: height 1.6s cubic-bezier(0.16, 1, 0.3, 1);
}

.exp-line--visible {
    height: 100%;
}

/* ── Item ────────────────────────────────────────────────── */
.exp-item {
    position: relative;
    display: flex;
    gap: 1.5rem;
    margin-bottom: 2rem;
    opacity: 0;
    transform: translateX(-16px);
    transition:
        opacity 0.55s ease,
        transform 0.55s cubic-bezier(0.34, 1.2, 0.64, 1);
}

.exp-item:last-child {
    margin-bottom: 0;
}

.exp-item--visible {
    opacity: 1;
    transform: translateX(0);
}

/* ── Nodo ────────────────────────────────────────────────── */
.exp-node {
    position: absolute;
    left: -29px;
    top: 18px;
    width: 14px;
    height: 14px;
    display: flex;
    align-items: center;
    justify-content: center;
    flex-shrink: 0;
}

.exp-node-dot {
    width: 10px;
    height: 10px;
    border-radius: 50%;
    background: var(--gray-1);
    border: 2px solid var(--gray-8);
    transition: border-color 0.3s ease, background 0.3s ease;
    position: relative;
    z-index: 1;
}

.exp-node--active .exp-node-dot {
    background: var(--green-9);
    border-color: var(--green-9);
    box-shadow: 0 0 10px rgba(0, 230, 118, 0.5);
}

/* Anillo pulsante para el nodo activo */
.exp-node-pulse {
    position: absolute;
    inset: -5px;
    border-radius: 50%;
    border: 1.5px solid rgba(0, 230, 118, 0.4);
    animation: node-pulse 2.2s ease-out infinite;
}

@keyframes node-pulse {
    0% {
        transform: scale(0.7);
        opacity: 0.7;
    }

    100% {
        transform: scale(2);
        opacity: 0;
    }
}

/* ── Card ────────────────────────────────────────────────── */
.exp-card {
    position: relative;
    flex: 1;
    background: var(--gray-2);
    border: 1px solid var(--gray-8);
    border-radius: 16px;
    padding: 1.5rem;
    display: flex;
    flex-direction: column;
    gap: 0.9rem;
    transition:
        background 0.25s ease,
        border-color 0.25s ease,
        transform 0.25s ease,
        box-shadow 0.25s ease;
    overflow: hidden;
}

.exp-card:hover {
    background: var(--gray-3);
    border-color: rgba(255, 255, 255, 0.1);
    transform: translateX(4px);
    box-shadow: 0 8px 36px rgba(0, 0, 0, 0.28);
}

/* Variante actual */
.exp-card--current {
    border-color: rgba(0, 230, 118, 0.2);
}

.exp-card--current:hover {
    border-color: rgba(0, 230, 118, 0.35);
    box-shadow: 0 8px 40px rgba(0, 230, 118, 0.08);
}

/* Glow izquierdo */
.exp-card-glow {
    position: absolute;
    left: 0;
    top: 0;
    bottom: 0;
    width: 3px;
    background: linear-gradient(to bottom,
            var(--green-9),
            rgba(0, 230, 118, 0.3));
    border-radius: 99px 0 0 99px;
}

/* ── Top row: fecha + badges ─────────────────────────────── */
.exp-card-top {
    display: flex;
    align-items: center;
    justify-content: space-between;
    gap: 0.75rem;
    flex-wrap: wrap;
}

.exp-card-meta {
    display: flex;
    align-items: center;
    gap: 0.35rem;
}

.exp-period {
    font-family: 'Outfit', sans-serif;
    font-size: 0.75rem;
    font-weight: 500;
    color: var(--gray-11);
    letter-spacing: 0.02em;
}

.exp-duration {
    font-family: 'Outfit', sans-serif;
    font-size: 0.72rem;
    color: var(--gray-11);
    opacity: 0.6;
}

.exp-badges {
    display: flex;
    align-items: center;
    gap: 0.4rem;
}

.exp-badge {
    font-family: 'Outfit', sans-serif;
    font-size: 0.6rem;
    font-weight: 600;
    letter-spacing: 0.06em;
    text-transform: uppercase;
    border-radius: 50px;
    padding: 0.18rem 0.6rem;
}

.exp-badge--type {
    color: var(--gray-11);
    background: rgba(255, 255, 255, 0.04);
    border: 1px solid var(--gray-8);
}

.exp-badge--current {
    display: flex;
    align-items: center;
    gap: 0.35rem;
    color: var(--green-9);
    background: var(--green-2);
    border: 1px solid rgba(0, 230, 118, 0.2);
}

.exp-badge-dot {
    width: 5px;
    height: 5px;
    border-radius: 50%;
    background: var(--green-9);
    box-shadow: 0 0 6px rgba(0, 230, 118, 0.7);
    animation: badge-dot 2s ease-in-out infinite;
}

@keyframes badge-dot {

    0%,
    100% {
        opacity: 1;
    }

    50% {
        opacity: 0.4;
    }
}

/* ── Heading ─────────────────────────────────────────────── */
.exp-card-heading {
    display: flex;
    flex-direction: column;
    gap: 0.3rem;
}

.exp-role {
    font-family: 'Syne', sans-serif;
    font-size: 1.1rem;
    font-weight: 700;
    color: var(--gray-12);
    margin: 0;
    letter-spacing: -0.02em;
}

.exp-company-row {
    display: flex;
    align-items: center;
    gap: 0.35rem;
}

.exp-company-icon {
    color: var(--gray-12);
    opacity: 0.6;
    flex-shrink: 0;
}

.exp-company {
    font-family: 'Outfit', sans-serif;
    font-size: 0.82rem;
    font-weight: 500;
    color: var(--green-11);
}

.exp-separator {
    color: var(--gray-8);
    font-size: 0.7rem;
}

.exp-location {
    font-family: 'Outfit', sans-serif;
    font-size: 0.78rem;
    color: var(--gray-11);
    opacity: 0.7;
}

/* ── Descripción ─────────────────────────────────────────── */
.exp-desc {
    font-family: 'Outfit', sans-serif;
    font-size: 0.84rem;
    color: var(--gray-11);
    line-height: 1.7;
    margin: 0;
}

/* ── Logros ──────────────────────────────────────────────── */
.exp-achievements {
    list-style: none;
    padding: 0;
    margin: 0;
    display: flex;
    flex-direction: column;
    gap: 0.4rem;
}

.exp-achievement {
    display: flex;
    align-items: center;
    gap: 0.55rem;
    font-family: 'Outfit', sans-serif;
    font-size: 0.78rem;
    color: var(--gray-11);
}

.exp-achievement svg {
    color: var(--green-9);
    flex-shrink: 0;
    opacity: 0.9;
}

/* ── Tags ────────────────────────────────────────────────── */
.exp-tags {
    display: flex;
    flex-wrap: wrap;
    gap: 0.35rem;
    padding-top: 10px;
    border-top: 1px solid var(--gray-8);
}

.exp-tag {
    font-family: 'Outfit', sans-serif;
    font-size: 0.62rem;
    font-weight: 500;
    color: var(--green-9);
    background: var(--green-2);
    border: 1px solid rgba(0, 230, 118, 0.15);
    padding: 0.18rem 0.55rem;
    border-radius: 50px;
    letter-spacing: 0.03em;
}

/* ── Responsive ──────────────────────────────────────────── */
@media (max-width: 600px) {
    .exp-timeline {
        padding-left: 28px;
    }

    .exp-node {
        left: -22px;
    }

    .exp-card {
        padding: 1.1rem;
    }

    .exp-card-top {
        flex-direction: column;
        align-items: flex-start;
    }

    .exp-company-row {
        flex-wrap: wrap;
    }
}
</style>