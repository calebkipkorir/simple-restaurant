<script setup>
import { onMounted } from 'vue'
import { gsap } from 'gsap'
import { ScrollTrigger } from 'gsap/ScrollTrigger'
import Navbar from './components/layout/Navbar.vue'
import Footer from './components/layout/Footer.vue'
import HeroSection from './components/sections/HeroSection.vue'
import AboutSection from './components/sections/AboutSection.vue'
import MenuServicesSection from './components/sections/MenuServicesSection.vue'
import GallerySection from './components/sections/GallerySection.vue'
import ExperienceSection from './components/sections/ExperienceSection.vue'
import TestimonialsSection from './components/sections/TestimonialsSection.vue'
import ContactSection from './components/sections/ContactSection.vue'

// Basic setup
gsap.registerPlugin(ScrollTrigger)

onMounted(() => {
  // Global intro animation
  gsap.from('body', { 
    opacity: 0, 
    duration: 1.2, 
    ease: "power2.out" 
  })
})
</script>

<template>
  <div class="relative min-h-screen bg-white dark:bg-luxury-dark text-slate-800 dark:text-gray-100 font-sans transition-colors duration-300">
    <Navbar />
    
    <main class="w-full">
      <HeroSection />
      <AboutSection />
      <MenuServicesSection />
      <GallerySection />
      <ExperienceSection />
      <TestimonialsSection />
      <ContactSection />
    </main>
    
    <Footer />
  </div>
</template>

<style>
/* Additional global transitions could be placed here if not in main CSS */
</style>
