<script setup>
import { onMounted, ref } from 'vue'
import { gsap } from 'gsap'
import { ScrollTrigger } from 'gsap/ScrollTrigger'

import culinaryImg from '../../assets/culinaryexperience.avif'
import roomsImg from '../../assets/roomsandsuites.avif'
import wellnessImg from '../../assets/wellness&spa.avif'

const sectionRef = ref(null)
const cardsRef = ref(null)

const services = [
  {
    title: "Culinary Experiences",
    description: "Savor exquisite dishes prepared by our Michelin-starred chefs, blending local ingredients with global techniques in a stunning panoramic setting.",
    image: culinaryImg,
    linkText: "View Menu"
  },
  {
    title: "Rooms & Suites",
    description: "Retreat to your private haven. Unwind in opulently designed suites offering breathtaking views, bespoke furnishings, and intuitive smart-room technology.",
    image: roomsImg,
    linkText: "Explore Rooms"
  },
  {
    title: "Wellness & Spa",
    description: "Rejuvenate mind, body, and soul in our holistic wellness center. Indulge in bespoke treatments, thermal baths, and personalized yoga sessions.",
    image: wellnessImg,
    linkText: "Discover Spa"
  }
]

onMounted(() => {
  gsap.registerPlugin(ScrollTrigger)

  gsap.from(cardsRef.value.children, {
    y: 50,
    opacity: 0,
    duration: 0.8,
    stagger: 0.2,
    ease: "power2.out",
    scrollTrigger: {
      trigger: sectionRef.value,
      start: "top 75%",
      toggleActions: "play none none reverse"
    }
  })
})
</script>

<template>
  <section ref="sectionRef" id="services" class="py-24 md:py-32 bg-slate-50 dark:bg-[#080d1e] overflow-hidden">
    <div class="container mx-auto px-6 md:px-12">
      
      <!-- Section Header -->
      <div class="text-center max-w-2xl mx-auto mb-16 md:mb-24">
        <p class="text-luxury-gold uppercase tracking-widest text-sm font-semibold mb-4">Exceptional Offerings</p>
        <h2 class="text-4xl md:text-5xl font-serif text-slate-900 dark:text-white font-medium mb-6">
          Tailored to your desires
        </h2>
        <div class="h-px w-24 bg-luxury-gold mx-auto"></div>
      </div>

      <!-- Services Cards -->
      <div ref="cardsRef" class="grid grid-cols-1 md:grid-cols-3 gap-8 lg:gap-12">
        <div 
          v-for="(service, index) in services" 
          :key="index"
          class="group bg-white dark:bg-luxury-surface border border-slate-100 dark:border-white/5 rounded-sm overflow-hidden hover:shadow-2xl transition-all duration-500 hover:-translate-y-2 flex flex-col"
        >
          <div class="relative h-64 overflow-hidden">
            <div class="absolute inset-0 bg-black/20 group-hover:bg-transparent transition-colors duration-500 z-10"></div>
            <img 
              :src="service.image" 
              :alt="service.title" 
              class="w-full h-full object-cover transform group-hover:scale-110 transition-transform duration-700" 
            />
          </div>
          
          <div class="p-8 flex flex-col flex-grow">
            <h3 class="text-2xl font-serif text-slate-900 dark:text-white mb-4 group-hover:text-luxury-gold transition-colors">
              {{ service.title }}
            </h3>
            <p class="text-slate-600 dark:text-gray-400 leading-relaxed mb-8 flex-grow">
              {{ service.description }}
            </p>
            <a href="#" class="inline-flex items-center gap-2 text-luxury-gold font-medium group/link uppercase text-sm tracking-widest mt-auto">
              {{ service.linkText }}
              <svg class="w-4 h-4 transform group-hover/link:translate-x-2 transition-transform" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17 8l4 4m0 0l-4 4m4-4H3"></path></svg>
            </a>
          </div>
        </div>
      </div>
      
    </div>
  </section>
</template>
