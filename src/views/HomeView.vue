<script setup>
import { onMounted } from 'vue'
import { gsap } from 'gsap'
import { ScrollTrigger } from 'gsap/ScrollTrigger'
import HeroSection from '../components/sections/HeroSection.vue'
import AboutSection from '../components/sections/AboutSection.vue'
import MenuServicesSection from '../components/sections/MenuServicesSection.vue'
import GallerySection from '../components/sections/GallerySection.vue'
import ExperienceSection from '../components/sections/ExperienceSection.vue'
import TestimonialsSection from '../components/sections/TestimonialsSection.vue'
import ContactSection from '../components/sections/ContactSection.vue'

onMounted(() => {
  gsap.registerPlugin(ScrollTrigger)
})
</script>

<template>
  <main class="w-full">
    <HeroSection />
    <AboutSection />
    <MenuServicesSection />
    <GallerySection />
    <ExperienceSection />
    <TestimonialsSection />
    <ContactSection />
  </main>
</template>
