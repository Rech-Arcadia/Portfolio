<script setup>
import { testimonials } from '../data/portfolioData.js';
</script>

<template>
  <section id="testimonials" class="section">
    <div class="container" style="text-align: center;">

      <h2 class="title-section" style="margin-bottom: 1.5rem;">Testimonials</h2>

      <button class="card"
        style="padding: 0.5rem 1.5rem; border-radius: 50px; background: transparent; cursor: pointer; color: white; margin-bottom: 3rem; font-size: 0.9rem; border: 1px solid var(--gray-8);">
        More testimonials &rarr;
      </button>

      <div class="grid-testimonials">
        <article v-for="testimonial in testimonials.slice(0, 2)" :key="testimonial.name" class="card card-body"
          style="text-align: left; padding: 2rem;">
          <p class="text-muted" style="margin-bottom: 2rem; font-size: 0.95rem; line-height: 1.8;">
            "{{ testimonial.text }}"
          </p>
          <div style="display: flex; align-items: center; gap: 1rem;">
            <img
              src="https://static.vecteezy.com/system/resources/previews/021/548/095/original/default-profile-picture-avatar-user-icon-person-icon-head-and-shoulders-profile-photo-free-png.png"
              alt="Client Avatar" style="width: 45px; height: 45px; border-radius: 50%;" />
            <div>
              <h4 style="font-size: 0.95rem; margin-bottom: 0.2rem;">{{ testimonial.name }}</h4>
              <span class="text-muted" style="font-size: 0.8rem;">{{ testimonial.company }}</span>
            </div>
          </div>
        </article>
      </div>

    </div>
  </section>
</template>