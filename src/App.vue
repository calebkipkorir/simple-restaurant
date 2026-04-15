<script setup>
import { onMounted } from 'vue'
import { gsap } from 'gsap'
import { ScrollTrigger } from 'gsap/ScrollTrigger'
import Navbar from './components/layout/Navbar.vue'
import Footer from './components/layout/Footer.vue'

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
    
    <router-view v-slot="{ Component }">
      <transition name="fade" mode="out-in">
        <component :is="Component" />
      </transition>
    </router-view>
    
    <Footer />
  </div>
</template>

<style>
/* Additional global transitions could be placed here if not in main CSS */
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s ease;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}
</style>
