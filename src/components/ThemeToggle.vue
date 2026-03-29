<script setup>
import { useDark, useToggle } from '@vueuse/core'

const isDark = useDark()
const toggleDark = useToggle(isDark)
</script>

<template>
    <button class="tt" :class="{ 'tt--dark': isDark }" @click="toggleDark()"
        :aria-label="isDark ? 'Cambiar a modo claro' : 'Cambiar a modo oscuro'" :aria-pressed="isDark" role="switch">
        <!-- Sol -->
        <svg class="tt-icon tt-icon--sun" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.75"
            stroke-linecap="round" stroke-linejoin="round">
            <circle cx="12" cy="12" r="4" />
            <line x1="12" y1="2" x2="12" y2="5" />
            <line x1="12" y1="19" x2="12" y2="22" />
            <line x1="4.22" y1="4.22" x2="6.34" y2="6.34" />
            <line x1="17.66" y1="17.66" x2="19.78" y2="19.78" />
            <line x1="2" y1="12" x2="5" y2="12" />
            <line x1="19" y1="12" x2="22" y2="12" />
            <line x1="4.22" y1="19.78" x2="6.34" y2="17.66" />
            <line x1="17.66" y1="6.34" x2="19.78" y2="4.22" />
        </svg>

        <!-- Luna -->
        <svg class="tt-icon tt-icon--moon" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.75"
            stroke-linecap="round" stroke-linejoin="round">
            <path d="M21 12.79A9 9 0 1 1 11.21 3 7 7 0 0 0 21 12.79z" />
        </svg>
    </button>
</template>

<style scoped>
.tt {
    position: relative;
    display: flex;
    align-items: center;
    justify-content: center;
    width: 36px;
    height: 36px;
    border-radius: 9px;
    border: 1px solid var(--border-color);
    background: transparent;
    cursor: pointer;
    color: var(--text-muted);
    transition:
        color 0.2s ease,
        border-color 0.2s ease,
        background 0.2s ease,
        transform 0.15s ease;
}

.tt:hover {
    color: var(--text-main);
    border-color: rgba(255, 255, 255, 0.18);
    background: rgba(255, 255, 255, 0.04);
}

.tt:focus-visible {
    outline: 2px solid var(--color-green);
    outline-offset: 2px;
}

.tt:active {
    transform: scale(0.9);
}

/* ── Iconos ──────────────────────────────────────────────── */
.tt-icon {
    position: absolute;
    width: 16px;
    height: 16px;
    transition:
        opacity 0.2s ease,
        transform 0.3s cubic-bezier(0.34, 1.3, 0.64, 1);
}

/* Light → sol visible */
.tt-icon--sun {
    opacity: 1;
    transform: rotate(0deg) scale(1);
}

.tt-icon--moon {
    opacity: 0;
    transform: rotate(30deg) scale(0.5);
}

/* Dark → luna visible */
.tt--dark .tt-icon--sun {
    opacity: 0;
    transform: rotate(-30deg) scale(0.5);
}

.tt--dark .tt-icon--moon {
    opacity: 1;
    transform: rotate(0deg) scale(1);
}
</style>