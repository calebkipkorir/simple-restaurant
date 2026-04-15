<script setup>
import { onMounted, ref } from 'vue'
import { gsap } from 'gsap'
import { ScrollTrigger } from 'gsap/ScrollTrigger'

const sectionRef = ref(null)
const imageRef = ref(null)
const textRef = ref(null)

onMounted(() => {
  gsap.registerPlugin(ScrollTrigger)

  let tl = gsap.timeline({
    scrollTrigger: {
      trigger: sectionRef.value,
      start: "top 80%",
      end: "bottom 80%",
      toggleActions: "play none none reverse"
    }
  })

  tl.from(imageRef.value, {
    x: -50,
    opacity: 0,
    duration: 1,
    ease: "power3.out"
  })
  .from(textRef.value.children, {
    y: 30,
    opacity: 0,
    duration: 0.8,
    stagger: 0.2,
    ease: "power3.out"
  }, "-=0.6")
})
</script>

<template>
  <section ref="sectionRef" id="about" class="py-24 md:py-32 bg-white dark:bg-luxury-dark overflow-hidden">
    <div class="container mx-auto px-6 md:px-12">
      <div class="flex flex-col lg:flex-row items-center gap-16 lg:gap-24">
        
        <!-- Image Area -->
        <div ref="imageRef" class="w-full lg:w-1/2 relative">
          <div class="relative rounded-sm overflow-hidden aspect-[4/5] md:aspect-square lg:aspect-[3/4]">
            <img 
              src="https://images.unsplash.com/photo-1582719508461-905c673771fd?q=80&w=1925&auto=format&fit=crop" 
              alt="Luxury Hotel Interior" 
              class="object-cover w-full h-full transform hover:scale-105 transition-transform duration-700" 
            />
          </div>
          <!-- Decorative element -->
          <div class="absolute -bottom-8 -right-8 w-2/3 aspect-square bg-slate-100 dark:bg-luxury-surface -z-10 rounded-sm"></div>
          <div class="absolute -top-6 -left-6 w-32 h-32 border-t-2 border-l-2 border-luxury-gold -z-10"></div>
        </div>

        <!-- Text Area -->
        <div ref="textRef" class="w-full lg:w-1/2">
          <p class="text-luxury-gold uppercase tracking-widest text-sm font-semibold mb-4 flex items-center gap-4">
            <span class="w-12 h-px bg-luxury-gold inline-block"></span>
            Heritage & Modernity
          </p>
          <h2 class="text-4xl md:text-5xl font-serif text-slate-900 dark:text-white font-medium mb-8 leading-tight">
            A sanctuary of calm <br/> in the heart of the city.
          </h2>
          <p class="text-slate-600 dark:text-gray-400 text-lg mb-6 leading-relaxed">
            Since 1985, Lumina has been a symbol of uncompromising luxury and impeccable service. We've crafted an environment where timeless elegance meets modern sophistication.
          </p>
          <p class="text-slate-600 dark:text-gray-400 text-lg mb-10 leading-relaxed">
            Every room, every meal, and every moment is designed to transform an ordinary stay into an extraordinary experience. Drift away in our award-winning spa or dine under the stars. 
          </p>
          
          <div class="grid grid-cols-2 gap-8 mb-10">
            <div>
              <p class="text-4xl font-serif text-luxury-gold mb-2">5<span class="text-2xl">★</span></p>
              <p class="text-sm text-slate-500 dark:text-gray-500 uppercase tracking-widest">Luxury Rating</p>
            </div>
            <div>
              <p class="text-4xl font-serif text-luxury-gold mb-2">320</p>
              <p class="text-sm text-slate-500 dark:text-gray-500 uppercase tracking-widest">Premium Suites</p>
            </div>
          </div>
          
          <a href="#history" class="inline-flex items-center gap-2 group text-slate-900 dark:text-white font-medium hover:text-luxury-gold transition-colors">
            <span class="pb-1 border-b border-transparent group-hover:border-luxury-gold transition-colors">Read Our Story</span>
            <svg class="w-4 h-4 transform group-hover:translate-x-2 transition-transform" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17 8l4 4m0 0l-4 4m4-4H3"></path></svg>
          </a>
        </div>
      </div>
    </div>
  </section>
</template>
