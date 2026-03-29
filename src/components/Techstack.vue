<template>
    <div class="tech-showcase">

        <!-- Fondo: glow + estrellas -->
        <div class="ts-bg" aria-hidden="true">
            <div class="ts-glow"></div>
            <span v-for="n in 32" :key="n" class="ts-star" :style="starStyle(n)"></span>
        </div>

        <!-- Fila horizontal de tecnologías -->
        <div class="ts-row">

            <!-- Techs izquierda -->
            <div class="ts-side ts-side--left">
                <div v-for="(tech, i) in leftTechs" :key="tech.name" class="ts-tech"
                    :style="{ '--c': tech.color, animationDelay: (i * 0.1) + 's' }">
                    <div class="ts-icon-wrap">
                        <span class="ts-icon-glow"></span>
                        <span class="ts-icon" v-html="tech.svg"></span>
                    </div>
                    <span class="ts-name">{{ tech.name }}</span>
                </div>
            </div>

            <!-- Vue — protagonista central -->
            <div class="ts-vue">
                <div class="ts-vue-ring ts-vue-ring--1" aria-hidden="true"></div>
                <div class="ts-vue-ring ts-vue-ring--2" aria-hidden="true"></div>
                <div class="ts-vue-icon-wrap">
                    <span class="ts-vue-glow"></span>
                    <svg class="ts-vue-svg" viewBox="0 0 261.76 226.69" xmlns="http://www.w3.org/2000/svg"
                        aria-label="Vue.js">
                        <path d="M161.096.001l-30.224 52.35L100.647.002H-.005L130.872 226.69 261.749.001z"
                            fill="#41b883" />
                        <path d="M161.096.001l-30.224 52.35L100.647.002H52.346l78.526 136.01L209.398.001z"
                            fill="#2d6a4f" />
                    </svg>
                </div>
                <span class="ts-vue-label">Vue 3</span>
            </div>

            <!-- Techs derecha -->
            <div class="ts-side ts-side--right">
                <div v-for="(tech, i) in rightTechs" :key="tech.name" class="ts-tech"
                    :style="{ '--c': tech.color, animationDelay: (i * 0.1 + 0.15) + 's' }">
                    <div class="ts-icon-wrap">
                        <span class="ts-icon-glow"></span>
                        <span class="ts-icon" v-html="tech.svg"></span>
                    </div>
                    <span class="ts-name">{{ tech.name }}</span>
                </div>
            </div>

        </div>
    </div>
</template>

<script setup>
const leftTechs = [
    {
        name: 'HTML5',
        color: '#ff3737',
        svg: `<svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="icon icon-tabler icons-tabler-outline icon-tabler-brand-html5"><path stroke="none" d="M0 0h24v24H0z" fill="none" /><path d="M20 4l-2 14.5l-6 2l-6 -2l-2 -14.5l16 0" /><path d="M15.5 8h-7l.5 4h6l-.5 3.5l-2.5 .75l-2.5 -.75l-.1 -.5" /></svg>`
    },
    {
        name: 'Figma',
        color: '#ff7237',
        svg: `<svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="icon icon-tabler icons-tabler-outline icon-tabler-brand-figma"><path stroke="none" d="M0 0h24v24H0z" fill="none" /><path d="M12 12a3 3 0 1 0 6 0a3 3 0 1 0 -6 0" /><path d="M6 6a3 3 0 0 1 3 -3h6a3 3 0 0 1 3 3a3 3 0 0 1 -3 3h-6a3 3 0 0 1 -3 -3" /><path d="M9 9a3 3 0 0 0 0 6h3m-3 0a3 3 0 1 0 3 3v-15" /></svg>`
    },
    {
        name: 'Vite',
        color: '#bd34fe',
        svg: `<svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="icon icon-tabler icons-tabler-outline icon-tabler-brand-vite"><path stroke="none" d="M0 0h24v24H0z" fill="none" /><path d="M10 4.5l6 -1.5l-2 6.5l2 -.5l-4 7v-5l-3 1l1 -7.5" /><path d="M15 6.5l7 -1.5l-10 17l-10 -17l7.741 1.5" /></svg>`
    },
]

const rightTechs = [
    {
        name: 'JavaScript',
        color: '#f7df1e',
        svg: `<svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="icon icon-tabler icons-tabler-outline icon-tabler-brand-javascript"><path stroke="none" d="M0 0h24v24H0z" fill="none"/><path d="M20 4l-2 14.5l-6 2l-6 -2l-2 -14.5l16 0" /><path d="M7.5 8h3v8l-2 -1" /><path d="M16.5 8h-2.5a.5 .5 0 0 0 -.5 .5v3a.5 .5 0 0 0 .5 .5h1.423a.5 .5 0 0 1 .495 .57l-.418 2.93l-2 .5" /></svg>`
    },
    {
        name: 'Tailwind',
        color: '#06b6d4',
        svg: `<svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="icon icon-tabler icons-tabler-outline icon-tabler-brand-tailwind"><path stroke="none" d="M0 0h24v24H0z" fill="none" /><path d="M11.667 6c-2.49 0 -4.044 1.222 -4.667 3.667c.933 -1.223 2.023 -1.68 3.267 -1.375c.71 .174 1.217 .68 1.778 1.24c.916 .912 2 1.968 4.288 1.968c2.49 0 4.044 -1.222 4.667 -3.667c-.933 1.223 -2.023 1.68 -3.267 1.375c-.71 -.174 -1.217 -.68 -1.778 -1.24c-.916 -.912 -1.975 -1.968 -4.288 -1.968m-4 6.5c-2.49 0 -4.044 1.222 -4.667 3.667c.933 -1.223 2.023 -1.68 3.267 -1.375c.71 .174 1.217 .68 1.778 1.24c.916 .912 1.975 1.968 4.288 1.968c2.49 0 4.044 -1.222 4.667 -3.667c-.933 1.223 -2.023 1.68 -3.267 1.375c-.71 -.174 -1.217 -.68 -1.778 -1.24c-.916 -.912 -1.975 -1.968 -4.288 -1.968" /></svg>`
    },
    {
        name: 'Node.js',
        color: '#339933',
        svg: `<svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="icon icon-tabler icons-tabler-outline icon-tabler-brand-nodejs"><path stroke="none" d="M0 0h24v24H0z" fill="none" /><path d="M9 9v8.044a2 2 0 0 1 -2.996 1.734l-1.568 -.9a3 3 0 0 1 -1.436 -2.561v-6.635a3 3 0 0 1 1.436 -2.56l6 -3.667a3 3 0 0 1 3.128 0l6 3.667a3 3 0 0 1 1.436 2.561v6.634a3 3 0 0 1 -1.436 2.56l-6 3.667a3 3 0 0 1 -3.128 0" /><path d="M17 9h-3.5a1.5 1.5 0 0 0 0 3h2a1.5 1.5 0 0 1 0 3h-3.5" /></svg>`
    },
]

function starStyle(n) {
    const h = (n * 2654435761) >>> 0
    return {
        left: (h % 100) + '%',
        top: ((h >> 8) % 100) + '%',
        width: (1 + (h % 2)) + 'px',
        height: (1 + (h % 2)) + 'px',
        animationDelay: ((h % 50) / 10) + 's',
        animationDuration: (2 + (h % 3)) + 's',
    }
}
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Outfit:wght@300;400;500&display=swap');

/* ── Contenedor ──────────────────────────────────────────── */
.tech-showcase {
    position: relative;
    width: 100%;
    padding: 1rem 0 2rem;
    /* overflow: hidden; */
    display: flex;
    align-items: center;
    justify-content: center;
}

/* ── Fondo ───────────────────────────────────────────────── */
.ts-bg {
    position: absolute;
    inset: 0;
    pointer-events: none;
}

.ts-glow {
    position: absolute;
    width: 640px;
    height: 640px;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    background: radial-gradient(ellipse at center,
            var(--bg-effect-1),
            var(--bg-effect-2),
            transparent 68%);
    border-radius: 50%;
    animation: glow-pulse 7s ease-in-out infinite alternate;
}

@keyframes glow-pulse {
    from {
        transform: translate(-50%, -50%) scale(1);
        opacity: 1;
    }

    to {
        transform: translate(-50%, -50%) scale(1.09);
        opacity: 0.78;
    }
}

.ts-star {
    position: absolute;
    border-radius: 50%;
    /* background: rgba(255, 255, 255, 0.6); */
    background: var(--gray-11);
    animation: twinkle var(--star-dur, 3s) ease-in-out infinite alternate;
}

@keyframes twinkle {
    from {
        opacity: 0.1;
    }

    to {
        opacity: 0.65;
    }
}

/* ── Fila principal ──────────────────────────────────────── */
.ts-row {
    position: relative;
    z-index: 1;
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 3rem;
}

/* ── Columnas laterales ──────────────────────────────────── */
.ts-side {
    display: flex;
    align-items: center;
    gap: 2rem;
}

/* ── Cada tecnología mini ────────────────────────────────── */
.ts-tech {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 0.55rem;
    cursor: default;
    animation: tech-in 0.5s ease both;
}

@keyframes tech-in {
    from {
        opacity: 0;
        transform: translateY(14px);
    }

    to {
        opacity: 1;
        transform: translateY(0);
    }
}

/* Wrap del icono: círculo oscuro sutil */
.ts-icon-wrap {
    position: relative;
    width: 52px;
    height: 52px;
    border-radius: 14px;
    background: rgba(255, 255, 255, 0.03);
    /* border: 1px solid rgba(255, 255, 255, 0.07); */
    border: 1px solid var(--gray-8);
    display: flex;
    align-items: center;
    justify-content: center;
    transition:
        background 0.3s ease,
        border-color 0.3s ease,
        transform 0.3s cubic-bezier(0.34, 1.4, 0.64, 1),
        box-shadow 0.3s ease;
}

.ts-tech:hover .ts-icon-wrap {
    background: color-mix(in srgb, var(--c) 10%, transparent);
    border-color: color-mix(in srgb, var(--c) 40%, transparent);
    transform: translateY(-5px) scale(1.08);
    box-shadow: 0 8px 28px color-mix(in srgb, var(--c) 22%, transparent);
}

/* Glow difuso detrás del icono */
.ts-icon-glow {
    position: absolute;
    inset: 0;
    border-radius: inherit;
    background: color-mix(in srgb, var(--c) 18%, transparent);
    opacity: 0;
    transition: opacity 0.3s ease;
    filter: blur(6px);
}

.ts-tech:hover .ts-icon-glow {
    opacity: 1;
}

/* SVG del icono */
.ts-icon {
    position: relative;
    display: flex;
    color: var(--c);
    transition: color 0.3s ease;
}

.ts-icon svg {
    width: 24px;
    height: 24px;
}

/* Nombre */
.ts-name {
    font-family: 'Outfit', sans-serif;
    font-size: 0.68rem;
    font-weight: 400;
    color: var(--gray-11);
    letter-spacing: 0.04em;
    transition: color 0.3s ease;
    white-space: nowrap;
}

.ts-tech:hover .ts-name {
    color: var(--gray-12);
}

/* ── Vue — protagonista ──────────────────────────────────── */
.ts-vue {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 0.8rem;
    position: relative;
    cursor: default;
}

/* Anillos pulsantes */
.ts-vue-ring {
    position: absolute;
    top: 50%;
    left: 50%;
    border-radius: 50%;
    border: 1px solid rgba(65, 184, 131, 0.15);
    pointer-events: none;
    transform: translate(-50%, -58%);
}

.ts-vue-ring--1 {
    width: 110px;
    height: 110px;
    animation: ring-out 3s ease-out infinite;
}

.ts-vue-ring--2 {
    width: 110px;
    height: 110px;
    animation: ring-out 3s ease-out infinite 1.5s;
}

@keyframes ring-out {
    0% {
        transform: translate(-50%, -58%) scale(0.7);
        opacity: 0.5;
    }

    100% {
        transform: translate(-50%, -58%) scale(1.9);
        opacity: 0;
    }
}

/* Wrap del logo Vue */
.ts-vue-icon-wrap {
    position: relative;
    width: 96px;
    height: 96px;
    display: flex;
    align-items: center;
    justify-content: center;
}

/* Glow detrás del logo */
.ts-vue-glow {
    position: absolute;
    inset: -12px;
    border-radius: 50%;
    background: radial-gradient(ellipse at center,
            rgba(65, 184, 131, 0.3) 0%,
            transparent 70%);
    animation: vue-glow-pulse 3s ease-in-out infinite alternate;
}

@keyframes vue-glow-pulse {
    from {
        opacity: 0.6;
        transform: scale(1);
    }

    to {
        opacity: 1;
        transform: scale(1.1);
    }
}

/* SVG Vue */
.ts-vue-svg {
    width: 72px;
    height: auto;
    position: relative;
    filter: drop-shadow(0 0 16px rgba(65, 184, 131, 0.45));
    animation: vue-float 5s ease-in-out infinite alternate;
    transition: filter 0.3s ease, transform 0.3s ease;
}

@keyframes vue-float {
    from {
        transform: translateY(0px);
    }

    to {
        transform: translateY(-7px);
    }
}

.ts-vue:hover .ts-vue-svg {
    filter: drop-shadow(0 0 28px rgba(65, 184, 131, 0.75));
    animation-play-state: paused;
    transform: translateY(-4px) scale(1.05);
}

/* Label Vue */
.ts-vue-label {
    font-family: 'Outfit', sans-serif;
    font-size: 0.72rem;
    font-weight: 500;
    letter-spacing: 0.1em;
    text-transform: uppercase;
    color: #41b883;
    opacity: 0.75;
}

/* ── Responsive ──────────────────────────────────────────── */
@media (max-width: 760px) {
    .ts-row {
        flex-direction: column;
        gap: 2.5rem;
    }

    .ts-side {
        gap: 1.5rem;
    }
}

@media (max-width: 420px) {
    .ts-side {
        gap: 1rem;
    }

    .ts-icon-wrap {
        width: 44px;
        height: 44px;
        border-radius: 10px;
    }

    .ts-icon svg {
        width: 20px;
        height: 20px;
    }
}
</style>