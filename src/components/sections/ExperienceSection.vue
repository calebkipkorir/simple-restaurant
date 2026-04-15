<script setup>
import { onMounted, ref } from 'vue'
import { gsap } from 'gsap'
import { ScrollTrigger } from 'gsap/ScrollTrigger'
import { Coffee, Wifi, Car, Plane, ShieldCheck, Dumbbell, Wine, Map } from 'lucide-vue-next'

const sectionRef = ref(null)
const featuresRef = ref(null)

const features = [
  { icon: Coffee, title: 'In-Room Breakfast', desc: 'Starting your morning luxuriously.' },
  { icon: Car, title: 'Valet Parking', desc: 'Seamless arrival and departure.' },
  { icon: Wifi, title: 'High-Speed Wi-Fi', desc: 'Stay connected effortlessly.' },
  { icon: Plane, title: 'Airport Transfers', desc: 'Chauffeur-driven luxury vehicles.' },
  { icon: Dumbbell, title: 'Fitness Center', desc: 'State-of-the-art equipment.' },
  { icon: Wine, title: 'Sommelier Service', desc: 'Expertly curated wine pairings.' },
  { icon: ShieldCheck, title: '24/7 Security', desc: 'Your privacy & safety ensured.' },
  { icon: Map, title: 'Concierge Desktop', desc: 'Tailored city excursions.' },
]

onMounted(() => {
  gsap.registerPlugin(ScrollTrigger)

  gsap.from(featuresRef.value.children, {
    y: 30,
    opacity: 0,
    duration: 0.6,
    stagger: 0.1,
    ease: "power2.out",
    scrollTrigger: {
      trigger: sectionRef.value,
      start: "top 70%",
    }
  })
})
</script>

<template>
  <section ref="sectionRef" class="py-24 bg-luxury-dark text-white relative overflow-hidden border-y border-white/5">
    <!-- Subtle Background Elements -->
    <div class="absolute top-0 right-0 w-1/2 h-full bg-gradient-to-l from-white/5 to-transparent z-0"></div>
    <div class="absolute -bottom-24 -left-24 w-64 h-64 border border-white/5 rounded-full z-0"></div>

    <div class="container mx-auto px-6 md:px-12 relative z-10">
      
      <div class="mb-16 md:text-center">
        <h2 class="text-3xl md:text-4xl font-serif text-white font-medium mb-4">
          The Lumina Experience
        </h2>
        <p class="text-gray-400 max-w-2xl mx-auto">
          Every detail of your stay has been meticulously curated to ensure supreme comfort and peace of mind.
        </p>
      </div>

      <div ref="featuresRef" class="grid grid-cols-2 md:grid-cols-4 gap-y-12 gap-x-8">
        <div 
          v-for="(feature, idx) in features" 
          :key="idx"
          class="flex flex-col items-start md:items-center text-left md:text-center group"
        >
          <div class="w-16 h-16 rounded-full bg-white/5 border border-white/10 flex items-center justify-center mb-6 group-hover:bg-luxury-gold group-hover:border-luxury-gold transition-colors duration-300">
            <component :is="feature.icon" class="w-7 h-7 text-luxury-gold group-hover:text-white transition-colors duration-300" />
          </div>
          <h3 class="text-lg font-serif mb-2 text-white">{{ feature.title }}</h3>
          <p class="text-sm text-gray-500">{{ feature.desc }}</p>
        </div>
      </div>
      
    </div>
  </section>
</template>
