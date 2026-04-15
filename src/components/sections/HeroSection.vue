<script setup>
import { onMounted, ref } from 'vue'
import { gsap } from 'gsap'
import { ScrollTrigger } from 'gsap/ScrollTrigger'

const heroRef = ref(null)
const overlayRef = ref(null)
const textRef = ref(null)

onMounted(() => {
  gsap.registerPlugin(ScrollTrigger)

  // Simple parallax on background
  gsap.to(overlayRef.value, {
    yPercent: 30,
    ease: "none",
    scrollTrigger: {
      trigger: heroRef.value,
      start: "top top",
      end: "bottom top",
      scrub: true
    }
  })

  // Fade in text gracefully
  gsap.from(textRef.value.children, {
    y: 50,
    opacity: 0,
    duration: 1,
    stagger: 0.2,
    ease: "power3.out",
    delay: 0.5
  })
})
</script>

<template>
  <section ref="heroRef" class="relative animate-section h-screen w-full flex items-center justify-center overflow-hidden">
    <!-- Background Image -->
    <div 
      ref="overlayRef" 
      class="absolute inset-0 w-full h-[130%] -top-[15%] bg-cover bg-center bg-no-repeat z-0"
      style="background-image: url('https://images.unsplash.com/photo-1520250497591-112f2f40a3f4?q=80&w=2070&auto=format&fit=crop');"
    ></div>
    
    <!-- Gradient Overlay -->
    <div class="absolute inset-0 bg-gradient-to-b from-black/60 via-black/40 to-black/80 z-10"></div>

    <!-- Content -->
    <div ref="textRef" class="relative z-20 container mx-auto px-6 text-center mt-16">
      <p class="text-luxury-gold uppercase tracking-[0.3em] text-sm md:text-base font-semibold mb-4">
        A symphony of elegance
      </p>
      <h1 class="text-5xl md:text-7xl lg:text-8xl font-serif text-white font-medium mb-6 leading-tight drop-shadow-xl">
        Discover the<br/>Art of Luxury
      </h1>
      <p class="text-gray-200 text-lg md:text-xl max-w-2xl mx-auto mb-10 font-light drop-shadow-md">
        Immerse yourself in unparalleled comfort and refined sophistication at Lumina. Your exclusive sanctuary awaits.
      </p>
      <div class="flex flex-col sm:flex-row justify-center items-center gap-4">
        <a href="#discover" class="bg-luxury-gold hover:bg-luxury-gold-hover text-white px-8 py-4 rounded-sm font-medium tracking-wide transition-colors duration-300 min-w-[200px]">
          Discover More
        </a>
        <a href="#book" class="bg-transparent border border-white hover:bg-white hover:text-slate-900 text-white px-8 py-4 rounded-sm font-medium tracking-wide transition-colors duration-300 min-w-[200px]">
          Reserve Your Stay
        </a>
      </div>
    </div>
    
    <!-- Scroll Down Indicator -->
    <div class="absolute bottom-10 left-1/2 -translate-x-1/2 z-20 flex flex-col items-center animate-bounce">
      <span class="text-white/70 text-xs uppercase tracking-widest mb-2 font-medium">Scroll</span>
      <div class="w-[1px] h-12 bg-gradient-to-b from-luxury-gold to-transparent"></div>
    </div>
  </section>
</template>
