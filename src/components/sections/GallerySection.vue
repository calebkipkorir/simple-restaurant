<script setup>
import { onMounted, ref } from 'vue'
import { gsap } from 'gsap'
import { ScrollTrigger } from 'gsap/ScrollTrigger'
import { Expand, X } from 'lucide-vue-next'

import gallery1 from '../../assets/gallery1.avif'
import gallery2 from '../../assets/gallery2.avif'
import gallery3 from '../../assets/gallery3.avif'
import gallery4 from '../../assets/gallery4.avif'
import gallery5 from '../../assets/gallery5.avif'
import gallery6 from '../../assets/gallery6.avif'

const sectionRef = ref(null)
const gridRef = ref(null)
const selectedImage = ref(null)

const images = [
  { src: gallery1, class: "col-span-2 row-span-2" },
  { src: gallery2, class: "col-span-1 row-span-1" },
  { src: gallery3, class: "col-span-1 row-span-1" },
  { src: gallery4, class: "col-span-1 row-span-2" },
  { src: gallery5, class: "col-span-1 row-span-1" },
  { src: gallery6, class: "col-span-2 row-span-1" }
]

onMounted(() => {
  gsap.registerPlugin(ScrollTrigger)

  gsap.from(gridRef.value.children, {
    scale: 0.9,
    opacity: 0,
    duration: 0.8,
    stagger: 0.15,
    ease: "power2.out",
    scrollTrigger: {
      trigger: sectionRef.value,
      start: "top 60%",
    }
  })
})

const openLightbox = (img) => {
  selectedImage.value = img
  document.body.style.overflow = 'hidden'
}

const closeLightbox = () => {
  selectedImage.value = null
  document.body.style.overflow = 'auto'
}
</script>

<template>
  <section ref="sectionRef" id="gallery" class="py-24 md:py-32 bg-white dark:bg-luxury-dark">
    <div class="container mx-auto px-6 md:px-12">
      <!-- Section Header -->
      <div class="flex flex-col md:flex-row justify-between items-end mb-16 gap-8">
        <div class="max-w-xl">
          <p class="text-luxury-gold uppercase tracking-widest text-sm font-semibold mb-4">Aesthetics & Design</p>
          <h2 class="text-4xl md:text-5xl font-serif text-slate-900 dark:text-white font-medium">
            Visual Journey
          </h2>
        </div>
        <a href="#" class="text-slate-900 dark:text-white border-b border-luxury-gold pb-1 hover:text-luxury-gold transition-colors uppercase text-sm tracking-widest font-medium">
          View Full Gallery
        </a>
      </div>

      <!-- Masonry Grid -->
      <div ref="gridRef" class="grid grid-cols-2 md:grid-cols-4 gap-4 auto-rows-[200px]">
        <div 
          v-for="(img, idx) in images" 
          :key="idx"
          :class="[img.class, 'relative group overflow-hidden cursor-pointer rounded-sm bg-slate-100 dark:bg-luxury-surface']"
          @click="openLightbox(img.src)"
        >
          <img 
            :src="img.src" 
            alt="Gallery entry" 
            class="w-full h-full object-cover transform group-hover:scale-110 transition-transform duration-700"
          />
          <div class="absolute inset-0 bg-black/40 opacity-0 group-hover:opacity-100 transition-opacity duration-300 flex items-center justify-center">
            <span class="bg-white/20 backdrop-blur-sm p-3 rounded-full text-white transform translate-y-4 group-hover:translate-y-0 transition-transform duration-300">
              <Expand class="w-6 h-6" />
            </span>
          </div>
        </div>
      </div>
    </div>

    <!-- Lightbox -->
    <transition name="fade">
      <div 
        v-if="selectedImage" 
        class="fixed inset-0 z-[100] bg-black/95 flex items-center justify-center p-4 backdrop-blur-sm"
        @click.self="closeLightbox"
      >
        <button 
          @click="closeLightbox" 
          class="absolute top-6 right-6 text-white/70 hover:text-white p-2 transition-colors z-[101]"
        >
          <X class="w-8 h-8" />
        </button>
        <img 
          :src="selectedImage" 
          class="max-w-full max-h-[90vh] object-contain rounded-sm shadow-2xl" 
          alt="Expanded view" 
        />
      </div>
    </transition>
  </section>
</template>

<style scoped>
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.3s ease;
}
.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}
</style
