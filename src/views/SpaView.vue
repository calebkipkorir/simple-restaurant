<script setup>
import { onMounted, ref } from 'vue'
import { gsap } from 'gsap'
import { ScrollTrigger } from 'gsap/ScrollTrigger'

const headerRef = ref(null)
const servicesRef = ref(null)

const treatments = [
  {
    name: 'Signature Lumina Massage',
    description: 'A blend of Swedish and deep tissue techniques tailored to your needs, enhanced with warm essential oils to melt away tension.',
    duration: '90 Minutes',
    price: '$210'
  },
  {
    name: 'Himalayan Salt Stone Ritual',
    description: 'Warm salt stones balance the central nervous system and nourish depleted cells, leaving you in a state of profound relaxation.',
    duration: '75 Minutes',
    price: '$180'
  },
  {
    name: 'Advanced Cellular Facial',
    description: 'A deeply restorative facial utilizing potent botanical extracts to boost collagen production and reveal a luminous complexion.',
    duration: '60 Minutes',
    price: '$150'
  }
]

onMounted(() => {
  gsap.registerPlugin(ScrollTrigger)

  // Header animation
  gsap.from(headerRef.value.children, {
    y: 50,
    opacity: 0,
    duration: 1,
    stagger: 0.2,
    ease: "power3.out",
    delay: 0.2
  })

  // List animation
  gsap.from('.treatment-item', {
    y: 30,
    opacity: 0,
    duration: 0.8,
    stagger: 0.15,
    ease: "power2.out",
    scrollTrigger: {
      trigger: servicesRef.value,
      start: "top 80%",
    }
  })
})
</script>

<template>
  <div class="min-h-screen pt-24 pb-12 bg-slate-50 dark:bg-[#080d1e]">
    <!-- Hero Section -->
    <section class="relative h-[60vh] w-full flex items-center justify-center overflow-hidden">
      <div 
        class="absolute inset-0 w-full h-full bg-cover bg-center"
        style="background-image: url('https://images.unsplash.com/photo-1540555700478-4be289fbecef?auto=format&fit=crop&w=1920&q=80');"
      ></div>
      <div class="absolute inset-0 bg-black/40"></div>
      
      <div ref="headerRef" class="relative z-10 text-center px-4">
        <p class="text-luxury-gold uppercase tracking-[0.2em] text-sm md:text-base font-semibold mb-4">
          Wellness & Rejuvenation
        </p>
        <h1 class="text-4xl md:text-6xl font-serif text-white font-medium drop-shadow-lg">
          Lumina Spa
        </h1>
      </div>
    </section>

    <!-- Services Section -->
    <section class="container mx-auto px-6 md:px-12 py-20 flex flex-col lg:flex-row gap-16" ref="servicesRef">
      
      <!-- Intro / Philosophy -->
      <div class="lg:w-1/3">
        <h2 class="text-3xl font-serif text-slate-900 dark:text-white mb-6">Holistic Healing</h2>
        <div class="h-px w-16 bg-luxury-gold mb-8"></div>
        <p class="text-slate-600 dark:text-gray-400 leading-relaxed mb-6">
          Step into a sanctuary where time stands still. At Lumina Spa, our philosophy is rooted in the earth's natural healing properties, integrating ancient rituals with modern wellness science to restore balance to mind, body, and spirit.
        </p>
        <img 
          src="https://images.unsplash.com/photo-1519823551278-64ac92734fb4?auto=format&fit=crop&w=600&q=80" 
          alt="Spa Details" 
          class="w-full h-64 object-cover shadow-lg"
        />
      </div>

      <!-- Treatment List -->
      <div class="lg:w-2/3">
        <h3 class="text-2xl font-serif text-luxury-gold mb-10 uppercase tracking-widest border-b border-slate-200 dark:border-white/10 pb-4">
          Curated Treatments
        </h3>
        
        <div class="space-y-10">
          <div v-for="treatment in treatments" :key="treatment.name" class="treatment-item p-6 bg-white dark:bg-luxury-surface border border-slate-100 dark:border-white/5 hover:shadow-xl transition-shadow duration-300">
            <div class="flex flex-col md:flex-row justify-between md:items-center gap-4 mb-4">
              <h4 class="text-xl font-serif text-slate-900 dark:text-gray-100">{{ treatment.name }}</h4>
              <div class="flex items-center gap-4">
                <span class="text-sm font-medium text-slate-500 dark:text-gray-400 border border-slate-200 dark:border-white/10 px-3 py-1 rounded-full">{{ treatment.duration }}</span>
                <span class="text-lg text-luxury-gold font-medium">{{ treatment.price }}</span>
              </div>
            </div>
            <p class="text-slate-600 dark:text-gray-400 leading-relaxed">
              {{ treatment.description }}
            </p>
          </div>
        </div>
        
        <div class="mt-12 text-center lg:text-left">
          <a href="#book" class="inline-block bg-transparent border border-luxury-gold text-luxury-gold hover:bg-luxury-gold hover:text-white px-8 py-3 font-medium tracking-wide transition-colors">
            Book an Appointment
          </a>
        </div>
      </div>

    </section>
  </div>
</template>
