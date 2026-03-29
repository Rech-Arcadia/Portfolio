<template>
    <section id="home" class="hero">

        <!-- Background: single centered glow + grain -->
        <div class="hero-bg" aria-hidden="true">
            <div class="glow-center"></div>
            <div class="grain"></div>
        </div>

        <div class="hero-body">

            <!-- Eyebrow -->
            <p class="eyebrow" :class="{ in: show }">
                <span class="eyebrow-line"></span>
                Web Developer Freelancer
                <span class="eyebrow-line"></span>
            </p>

            <!-- Main headline -->
            <h1 class="headline" :class="{ in: show }">
                <span class="line line-1">¿Buscas resultados</span>
                <span class="line line-2">reales en la <em>web?</em></span>
            </h1>

            <!-- Sub -->
            <p class="sub" :class="{ in: show }">
                Desarrollo soluciones web limpias, rápidas y mantenibles.<br class="br" />
                De la idea al producto, sin complicaciones.
            </p>

            <!-- Actions -->
            <div class="actions" :class="{ in: show }">
                <Techstack />
            </div>

            <!-- Scroll hint -->
            <div class="scroll-hint" :class="{ in: show }" aria-hidden="true">
                <div class="scroll-track">
                    <div class="scroll-thumb"></div>
                </div>
                <span>scroll</span>
            </div>

        </div>
    </section>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import Techstack from './Techstack.vue'

const show = ref(false)

function go(id) {
    document.getElementById(id)?.scrollIntoView({ behavior: 'smooth' })
}

onMounted(() => requestAnimationFrame(() => { show.value = true }))
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Montserrat:ital,wght@0,100..900;1,100..900&display=swap');

/* ─── Shell ──────────────────────────────────────────────── */
.hero {
    position: relative;
    min-height: 100svh;
    display: flex;
    align-items: center;
    justify-content: center;
    overflow: hidden;
    text-align: center;
}

/* ─── Background ─────────────────────────────────────────── */
.hero-bg {
    position: absolute;
    inset: 0;
    z-index: 0;
    pointer-events: none;
}

.glow-center {
    position: absolute;
    width: 900px;
    height: 900px;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -52%);
    background: radial-gradient(ellipse at center,
            rgba(0, 100, 60, 0.38) 0%,
            rgba(0, 60, 36, 0.18) 40%,
            transparent 70%);
    border-radius: 50%;
    animation: breathe 8s ease-in-out infinite alternate;
}

@keyframes breathe {
    from {
        transform: translate(-50%, -52%) scale(1);
        opacity: 1;
    }

    to {
        transform: translate(-50%, -52%) scale(1.08);
        opacity: 0.85;
    }
}

.grain {
    position: absolute;
    inset: 0;
    opacity: 0.055;
    background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='300' height='300'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.75' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='300' height='300' filter='url(%23n)'/%3E%3C/svg%3E");
    background-size: 200px 200px;
}

/* ─── Body ───────────────────────────────────────────────── */
.hero-body {
    position: relative;
    z-index: 1;
    display: flex;
    flex-direction: column;
    align-items: center;
    padding: 8rem 1.5rem 5rem;
    max-width: 820px;
    margin: 0 auto;
}

/* ─── Eyebrow ────────────────────────────────────────────── */
.eyebrow {
    display: flex;
    align-items: center;
    gap: 0.9rem;
    font-family: 'Montserrat', sans-serif;
    font-size: 0.72rem;
    font-weight: 500;
    letter-spacing: 0.18em;
    text-transform: uppercase;
    color: var(--green-9);
    margin-bottom: 2rem;

    opacity: 0;
    transform: translateY(10px);
    transition: opacity 0.7s ease, transform 0.7s ease;
}

.eyebrow.in {
    opacity: 1;
    transform: translateY(0);
}

.eyebrow-line {
    display: block;
    width: 32px;
    height: 1px;
    background: currentColor;
    opacity: 0.5;
}

/* ─── Headline ───────────────────────────────────────────── */
.headline {
    font-family: 'Montserrat', sans-serif;
    font-weight: 700;
    /* font-size: clamp(3rem, 7vw, 5.6rem); */
    font-size: 80px;
    line-height: 1.04;
    letter-spacing: -0.025em;
    color: var(--gray-12);
    margin-bottom: 2rem;
}

.line {
    display: block;
    opacity: 0;
    transform: translateY(24px);
    transition: opacity 0.7s ease, transform 0.7s ease;
}

.headline.in .line-1 {
    opacity: 1;
    transform: translateY(0);
    transition-delay: 0.1s;
}

.headline.in .line-2 {
    opacity: 1;
    transform: translateY(0);
    transition-delay: 0.22s;
}

.headline em {
    font-style: italic;
    font-weight: 300;
    color: var(--green-9);
}

/* ─── Sub ────────────────────────────────────────────────── */
.sub {
    font-family: 'Montserrat', sans-serif;
    font-size: 1.05rem;
    font-weight: 300;
    line-height: 1.8;
    color: var(--gray-11);
    max-width: 500px;
    margin-bottom: 2.8rem;

    opacity: 0;
    transform: translateY(16px);
    transition: opacity 0.7s ease 0.32s, transform 0.7s ease 0.32s;
}

.sub.in {
    opacity: 1;
    transform: translateY(0);
}

/* ─── Actions ────────────────────────────────────────────── */
.actions {
    display: flex;
    align-items: center;
    gap: 1rem;
    flex-wrap: wrap;
    justify-content: center;
    margin-bottom: 5rem;

    opacity: 0;
    transform: translateY(12px);
    transition: opacity 0.7s ease 0.44s, transform 0.7s ease 0.44s;
}

.actions.in {
    opacity: 1;
    transform: translateY(0);
}

.cta-main {
    display: inline-flex;
    align-items: center;
    gap: 0.5rem;
    padding: 0.8rem 1.8rem;
    background: var(--green-9);
    color: #061208;
    font-family: 'Montserrat', sans-serif;
    font-weight: 500;
    font-size: 0.9rem;
    border-radius: 50px;
    text-decoration: none;
    letter-spacing: 0.02em;
    transition: transform 0.22s ease, box-shadow 0.22s ease, background 0.22s ease;
}

.cta-main:hover {
    transform: translateY(-3px);
    box-shadow: 0 12px 36px rgba(0, 230, 118, 0.22);
    background: #1aeb88;
}

.cta-ghost {
    display: inline-flex;
    align-items: center;
    padding: 0.8rem 1.6rem;
    font-family: 'Montserrat', sans-serif;
    font-weight: 400;
    font-size: 0.9rem;
    color: var(--gray-11);
    border: 1px solid rgba(255, 255, 255, 0.1);
    border-radius: 50px;
    text-decoration: none;
    letter-spacing: 0.02em;
    transition: color 0.22s ease, border-color 0.22s ease;
}

.cta-ghost:hover {
    color: var(--gray-12);
    border-color: rgba(255, 255, 255, 0.25);
}

/* ─── Scroll hint ────────────────────────────────────────── */
.scroll-hint {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 0.5rem;
    opacity: 0;
    transition: opacity 0.7s ease 0.9s;
}

.scroll-hint.in {
    opacity: 0.35;
}

.scroll-track {
    width: 22px;
    height: 36px;
    border: 1.5px solid var(--gray-11);
    border-radius: 50px;
    display: flex;
    justify-content: center;
    padding: 4px;
}

.scroll-thumb {
    width: 4px;
    height: 8px;
    background: var(--green-9);
    border-radius: 99px;
    animation: scroll-bounce 2s ease-in-out infinite;
}

@keyframes scroll-bounce {

    0%,
    100% {
        transform: translateY(0);
        opacity: 1;
    }

    60% {
        transform: translateY(10px);
        opacity: 0.3;
    }
}

.scroll-hint span {
    font-family: 'Montserrat', sans-serif;
    font-size: 0.6rem;
    letter-spacing: 0.15em;
    text-transform: uppercase;
    color: var(--gray-11);
}

/* ─── Responsive ─────────────────────────────────────────── */
@media (max-width: 600px) {
    .headline {
        font-size: 2.6rem;
    }

    .br {
        display: none;
    }

    .eyebrow-line {
        width: 20px;
    }
}
</style>