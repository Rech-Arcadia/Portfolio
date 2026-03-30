<script setup>
// Importamos todos los componentes
import AppHeader from './components/AppHeader.vue'
import HeroSection from './components/HeroSection.vue'
import PortfolioSection from './components/PortfolioSection.vue'
import ProjectsSection from './components/ProjectsSection.vue'
import TestimonialsSection from './components/TestimonialsSection.vue'
import AppFooter from './components/AppFooter.vue'
import ExperienceSection from './components/ExperienceSection.vue'
</script>

<template>
  <div class="app-wrapper">

    <AppHeader />

    <main>
      <HeroSection />

      <PortfolioSection />

      <ProjectsSection />

      <ExperienceSection />

      <TestimonialsSection />
    </main>

    <AppFooter />

  </div>
</template>

<style>
.app-wrapper {
  width: 100%;
  overflow-x: hidden;
}
</style>