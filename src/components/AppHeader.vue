<template>
    <header class="app-header" :class="{ 'scrolled': isScrolled }">
        <div class="header-inner container">

            <!-- Logo / Brand -->
            <a href="#home" class="brand" @click.prevent="scrollTo('home')">
                <div class="brand-avatar">R</div>
                <div class="brand-text">
                    <span class="brand-name">Ricardo Arcadia Avalos</span>
                    <span class="brand-role">Web Developer</span>
                </div>
            </a>

            <!-- Desktop Nav -->
            <nav class="nav-desktop" aria-label="Main navigation">
                <a v-for="link in navLinks" :key="link.id" :href="`#${link.id}`" class="nav-link"
                    :class="{ active: activeSection === link.id }" @click.prevent="scrollTo(link.id)">
                    {{ link.label }}
                    <span class="nav-indicator"></span>
                </a>
            </nav>

            <!-- CTA + Hamburger -->
            <div class="header-actions">
                <a href="#contact" class="btn-cta" @click.prevent="scrollTo('contact')">
                    <span class="btn-cta-text">Contactame</span>
                    <svg class="btn-cta-icon" xmlns="http://www.w3.org/2000/svg" width="14" height="14"
                        viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round"
                        stroke-linejoin="round">
                        <path d="M21 15a2 2 0 0 1-2 2H7l-4 4V5a2 2 0 0 1 2-2h14a2 2 0 0 1 2 2z" />
                    </svg>
                    <span class="btn-shimmer"></span>
                </a>

                <button class="hamburger" :class="{ open: menuOpen }" @click="menuOpen = !menuOpen"
                    aria-label="Toggle menu">
                    <span></span>
                    <span></span>
                    <span></span>
                </button>
                <ThemeToggle />
            </div>
        </div>

        <!-- Mobile Menu -->
        <Transition name="mobile-menu">
            <div v-if="menuOpen" class="mobile-nav">
                <a v-for="link in navLinks" :key="link.id" :href="`#${link.id}`" class="mobile-link"
                    :class="{ active: activeSection === link.id }"
                    @click.prevent="() => { scrollTo(link.id); menuOpen = false }">
                    <span class="mobile-link-dot"></span>
                    {{ link.label }}
                </a>
                <a href="#contact" class="btn-cta mobile-cta"
                    @click.prevent="() => { scrollTo('contact'); menuOpen = false }">
                    <span class="btn-cta-text">Let's chat</span>
                    <svg xmlns="http://www.w3.org/2000/svg" width="14" height="14" viewBox="0 0 24 24" fill="none"
                        stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round">
                        <path d="M21 15a2 2 0 0 1-2 2H7l-4 4V5a2 2 0 0 1 2-2h14a2 2 0 0 1 2 2z" />
                    </svg>
                </a>
            </div>
        </Transition>
    </header>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'
import ThemeToggle from './ThemeToggle.vue'

const navLinks = [
    { id: 'home', label: 'Home' },
    { id: 'about', label: 'Sobre mí' },
    { id: 'projects', label: 'Proyectos' },
    { id: 'tips', label: 'Consejos de Vue' },
    { id: 'blog', label: 'Blog' },
    { id: 'testimonials', label: 'Testimonios' },
]

const isScrolled = ref(false)
const menuOpen = ref(false)
const activeSection = ref('home')

function scrollTo(id) {
    const el = document.getElementById(id)
    if (el) el.scrollIntoView({ behavior: 'smooth' })
}

function onScroll() {
    isScrolled.value = window.scrollY > 20

    // Detect active section
    for (const link of [...navLinks].reverse()) {
        const el = document.getElementById(link.id)
        if (el && window.scrollY >= el.offsetTop - 120) {
            activeSection.value = link.id
            break
        }
    }
}

onMounted(() => window.addEventListener('scroll', onScroll, { passive: true }))
onUnmounted(() => window.removeEventListener('scroll', onScroll))
</script>

<style scoped>
/* ─── Import font ───────────────────────────────────────── */
@import url('https://fonts.googleapis.com/css2?family=Syne:wght@500;600;700;800&display=swap');


/* ─── Header shell ──────────────────────────────────────── */
.app-header {
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    z-index: 100;
    transition: background 0.4s ease, border-color 0.4s ease, box-shadow 0.4s ease;
    border-bottom: 1px solid transparent;
}

.app-header.scrolled {
    /* background: rgba(16, 16, 16, 0.82); */
    background: var(--scrolled-bg);
    backdrop-filter: blur(20px) saturate(160%);
    /* -webkit-backdrop-filter: blur(20px) saturate(160%); */
    border-bottom-color: var(--gray-2);
    box-shadow: 0 4px 40px rgba(0, 0, 0, 0.4);
}

.header-inner {
    display: flex;
    align-items: center;
    justify-content: space-between;
    height: 70px;
}

/* ─── Brand ─────────────────────────────────────────────── */
.brand {
    display: flex;
    align-items: center;
    gap: 0.75rem;
    text-decoration: none;
}

.brand-avatar {
    width: 38px;
    height: 38px;
    border-radius: 10px;
    background: linear-gradient(135deg, var(--green-9) 0%, #00b356 100%);
    color: #0a1a0f;
    font-family: 'Syne', sans-serif;
    font-weight: 800;
    font-size: 1.1rem;
    display: flex;
    align-items: center;
    justify-content: center;
    flex-shrink: 0;
    transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.brand:hover .brand-avatar {
    transform: rotate(-6deg) scale(1.05);
    box-shadow: 0 0 18px rgba(0, 230, 118, 0.35);
}

.brand-text {
    display: flex;
    flex-direction: column;
    line-height: 1.2;
}

.brand-name {
    font-family: 'Syne', sans-serif;
    font-weight: 700;
    font-size: 0.95rem;
    color: var(--gray-12);
    letter-spacing: -0.01em;
}

.brand-role {
    font-size: 0.7rem;
    font-weight: 500;
    color: var(--green-9);
    letter-spacing: 0.06em;
    text-transform: uppercase;
}

/* ─── Desktop nav ───────────────────────────────────────── */
.nav-desktop {
    display: flex;
    align-items: center;
    gap: 0.25rem;
}

.nav-link {
    position: relative;
    padding: 0.4rem 0.75rem;
    font-size: 0.875rem;
    font-weight: 500;
    color: var(--gray-11);
    text-decoration: none;
    border-radius: 6px;
    transition: color 0.25s ease, background 0.25s ease;
    letter-spacing: 0.01em;
}

.nav-link::after {
    content: '';
    position: absolute;
    bottom: -1px;
    left: 50%;
    transform: translateX(-50%) scaleX(0);
    width: 20px;
    height: 2px;
    background: var(--green-9);
    border-radius: 99px;
    transition: transform 0.25s cubic-bezier(0.34, 1.56, 0.64, 1);
}

.nav-link:hover {
    color: var(--gray-12);
    background: rgba(255, 255, 255, 0.04);
}

.nav-link.active {
    color: var(--gray-12);
}

.nav-link.active::after {
    transform: translateX(-50%) scaleX(1);
}

/* ─── CTA Button ────────────────────────────────────────── */
.header-actions {
    display: flex;
    align-items: center;
    gap: 0.75rem;
}

.btn-cta {
    position: relative;
    display: inline-flex;
    align-items: center;
    gap: 0.5rem;
    padding: 0.5rem 1.1rem;
    background: var(--green-9);
    color: var(--gray-1);
    font-weight: 700;
    font-size: 0.85rem;
    border-radius: 50px;
    text-decoration: none;
    overflow: hidden;
    transition: transform 0.2s ease, box-shadow 0.2s ease;
    letter-spacing: 0.01em;
}

.btn-cta:hover {
    transform: translateY(-2px);
    box-shadow: 0 6px 24px rgba(0, 230, 118, 0.3);
}

/* Shimmer sweep */
.btn-shimmer {
    position: absolute;
    top: 0;
    left: -60%;
    width: 40%;
    height: 100%;
    background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.35), transparent);
    transform: skewX(-20deg);
    animation: shimmer 3s infinite 1s;
}

@keyframes shimmer {
    0% {
        left: -60%;
    }

    40% {
        left: 120%;
    }

    100% {
        left: 120%;
    }
}

/* ─── Hamburger ─────────────────────────────────────────── */
.hamburger {
    display: none;
    flex-direction: column;
    justify-content: center;
    gap: 5px;
    width: 36px;
    height: 36px;
    background: transparent;
    border: 1px solid var(--gray-8);
    border-radius: 8px;
    cursor: pointer;
    padding: 0 8px;
    transition: border-color 0.2s ease;
}

.hamburger:hover {
    border-color: var(--gray-11);
}

.hamburger span {
    display: block;
    height: 1.5px;
    background: var(--gray-11);
    border-radius: 99px;
    transition: transform 0.3s ease, opacity 0.3s ease, width 0.3s ease;
    transform-origin: center;
}

/* X state */
.hamburger.open span:nth-child(1) {
    transform: translateY(6.5px) rotate(45deg);
    background: var(--gray-12);
}

.hamburger.open span:nth-child(2) {
    opacity: 0;
    transform: scaleX(0);
}

.hamburger.open span:nth-child(3) {
    transform: translateY(-6.5px) rotate(-45deg);
    background: var(--gray-12);
}

/* ─── Mobile nav ────────────────────────────────────────── */
.mobile-nav {
    display: flex;
    flex-direction: column;
    gap: 0.25rem;
    padding: 1rem 1.5rem 1.5rem;
    /* background: rgba(16, 16, 16, 0.96); */
    background: var(--gray-1);
    backdrop-filter: blur(24px);
    border-bottom: 1px solid var(--gray-8);
}

.mobile-link {
    display: flex;
    align-items: center;
    gap: 0.75rem;
    padding: 0.65rem 0.75rem;
    font-size: 0.95rem;
    font-weight: 500;
    color: var(--gray-11);
    text-decoration: none;
    border-radius: 8px;
    transition: color 0.2s ease, background 0.2s ease;
}

.mobile-link:hover,
.mobile-link.active {
    color: var(--gray-12);
    background: rgba(255, 255, 255, 0.04);
}

.mobile-link-dot {
    width: 6px;
    height: 6px;
    border-radius: 50%;
    background: var(--gray-8);
    flex-shrink: 0;
    transition: background 0.2s ease;
}

.mobile-link.active .mobile-link-dot {
    background: var(--green-9);
    box-shadow: 0 0 6px rgba(0, 230, 118, 0.6);
}

.mobile-cta {
    margin-top: 0.75rem;
    justify-content: center;
}

/* ─── Transition ────────────────────────────────────────── */
.mobile-menu-enter-active,
.mobile-menu-leave-active {
    transition: opacity 0.25s ease, transform 0.25s ease;
}

.mobile-menu-enter-from,
.mobile-menu-leave-to {
    opacity: 0;
    transform: translateY(-8px);
}

/* ─── Responsive ────────────────────────────────────────── */
@media (max-width: 900px) {
    .nav-desktop {
        display: none;
    }

    .hamburger {
        display: flex;
    }
}

@media (max-width: 480px) {
    .brand-role {
        display: none;
    }

    .btn-cta:not(.mobile-cta) {
        display: none;
    }
}
</style>