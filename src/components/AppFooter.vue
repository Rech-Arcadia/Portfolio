<script setup>
import { footerLinks } from '../data/portfolioData.js';
</script>

<template>
  <footer style="padding: 5rem 0 2rem; border-top: 1px solid var(--gray-8);">
    <div class="container footer-grid">

      <div v-for="(links, category) in footerLinks" :key="category">
        <h4 style="margin-bottom: 1.5rem; font-size: 0.9rem; font-weight: 600; text-transform: capitalize;">{{ category
        }}</h4>
        <ul style="display: flex; flex-direction: column; gap: 1rem;">
          <li v-for="link in links" :key="link">
            <a href="#" class="text-muted" style="font-size: 0.85rem;">{{ link }}</a>
          </li>
        </ul>
      </div>

    </div>

    <div class="container"
      style="border-top: 1px solid var(--gray-8); padding-top: 2rem; margin-top: 4rem; display: flex; flex-wrap: wrap; justify-content: space-between; align-items: center; gap: 1rem;">
      <span class="text-muted" style="font-size: 0.85rem;">Copyright © {{ new Date().getFullYear() }} Ricardo Arcadia
        Avalos.</span>

      <div style="display: flex; gap: 1.5rem; align-items: center;">
        <a href="#" class="text-muted" style="font-size: 0.85rem;">X</a>
        <a href="#" class="text-muted" style="font-size: 0.85rem;">GitHub</a>
        <a href="#" class="text-muted" style="font-size: 0.85rem;">LinkedIn</a>
        <a href="#" class="text-muted" style="font-size: 0.85rem;">YouTube</a>
        <button
          style="background: transparent; border: 1px solid var(--gray-8); color: var(--gray-12); padding: 0.2rem 0.8rem; border-radius: 4px; font-size: 0.8rem; cursor: pointer;">
          us English ⌄
        </button>
      </div>
    </div>
  </footer>
</template>

<style scoped>
.footer-grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 3rem;
}

@media (min-width: 768px) {
  .footer-grid {
    grid-template-columns: repeat(4, 1fr);
  }
}
</style>