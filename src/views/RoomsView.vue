<script setup>
import { onMounted, ref } from 'vue'
import { gsap } from 'gsap'
import { ScrollTrigger } from 'gsap/ScrollTrigger'

const headerRef = ref(null)
const roomsRef = ref(null)

const rooms = [
  {
    name: 'Presidential Suite',
    description: 'Our most opulent offering. Spanning 2,000 square feet, this suite features a private terrace with panoramic ocean views, a dedicated dining area, and a personal butler service available 24/7.',
    amenities: ['Private Terrace', '24/7 Butler Service', 'Marble Bath', 'Ocean View'],
    image: 'https://images.unsplash.com/photo-1582719478250-c89fae4c85b2?auto=format&fit=crop&w=1000&q=80',
    price: 'From $1,500 / night'
  },
  {
    name: 'Luxury Ocean-View Room',
    description: 'Immerse yourself in serenity. These rooms are designed with bespoke furnishings, intuitive smart-room technology, and floor-to-ceiling windows that perfectly frame the breathtaking coastline.',
    amenities: ['Smart Technology', 'King Size Bed', 'Premium Minibar', 'Balcony'],
    image: 'https://images.unsplash.com/photo-1590490359854-ceba1fa3ab0c?auto=format&fit=crop&w=1000&q=80',
    price: 'From $650 / night'
  },
  {
    name: 'Executive Garden Suite',
    description: 'A tranquil retreat overlooking our meticulously landscaped botanical gardens. Features a separate living area, perfect for both relaxation and quiet contemplation.',
    amenities: ['Garden View', 'Deep Soaking Tub', 'Separate Living Area', 'Espresso Machine'],
    image: 'https://images.unsplash.com/photo-1611892440504-42a792e24d32?auto=format&fit=crop&w=1000&q=80',
    price: 'From $850 / night'
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

  // Rooms animation
  gsap.utils.toArray('.room-card').forEach((card, i) => {
    gsap.from(card, {
      y: 50,
      opacity: 0,
      duration: 0.8,
      ease: "power2.out",
      scrollTrigger: {
        trigger: card,
        start: "top 85%",
      }
    })
  })
})
</script>

<template>
  <div class="min-h-screen pt-24 pb-12 bg-slate-50 dark:bg-[#080d1e]">
    <!-- Hero Section -->
    <section class="relative h-[60vh] w-full flex items-center justify-center overflow-hidden">
      <div 
        class="absolute inset-0 w-full h-full bg-cover bg-center"
        style="background-image: url('https://images.unsplash.com/photo-1590490360182-c33d57733427?auto=format&fit=crop&w=1920&q=80');"
      ></div>
      <div class="absolute inset-0 bg-black/40"></div>
      
      <div ref="headerRef" class="relative z-10 text-center px-4">
        <p class="text-luxury-gold uppercase tracking-[0.2em] text-sm md:text-base font-semibold mb-4">
          Your Personal Haven
        </p>
        <h1 class="text-4xl md:text-6xl font-serif text-white font-medium drop-shadow-lg">
          Rooms & Suites
        </h1>
      </div>
    </section>

    <!-- Rooms List Section -->
    <section class="container mx-auto px-6 md:px-12 py-20" ref="roomsRef">
      <div class="max-w-3xl mx-auto text-center mb-20">
        <h2 class="text-3xl font-serif text-slate-900 dark:text-white mb-6">Unparalleled Comfort</h2>
        <div class="h-px w-16 bg-luxury-gold mx-auto"></div>
        <p class="mt-8 text-slate-600 dark:text-gray-400 leading-relaxed">
          Every space at Lumina is a testament to refined design and meticulous attention to detail. Experience true relaxation in our exquisitely appointed rooms and suites.
        </p>
      </div>

      <div class="space-y-24">
        <div 
          v-for="(room, index) in rooms" 
          :key="room.name" 
          class="room-card flex flex-col md:flex-row gap-12 items-center"
          :class="{'md:flex-row-reverse': index % 2 !== 0}"
        >
          <!-- Image -->
          <div class="w-full md:w-1/2 overflow-hidden shadow-2xl">
            <img 
              :src="room.image" 
              :alt="room.name" 
              class="w-full h-[400px] object-cover hover:scale-105 transition-transform duration-700" 
            />
          </div>
          
          <!-- Details -->
          <div class="w-full md:w-1/2 flex flex-col justify-center">
            <h3 class="text-3xl font-serif text-slate-900 dark:text-white mb-4">{{ room.name }}</h3>
            <p class="text-slate-600 dark:text-gray-400 leading-relaxed mb-8">
              {{ room.description }}
            </p>
            
            <div class="mb-8">
              <h4 class="text-sm uppercase tracking-widest text-luxury-gold font-medium mb-4">Amenities</h4>
              <ul class="grid grid-cols-2 gap-y-2 gap-x-4">
                <li v-for="amenity in room.amenities" :key="amenity" class="flex items-center gap-2 text-sm text-slate-700 dark:text-gray-300">
                  <div class="w-1.5 h-1.5 rounded-full bg-luxury-gold"></div>
                  {{ amenity }}
                </li>
              </ul>
            </div>
            
            <div class="flex items-center justify-between pt-6 border-t border-slate-200 dark:border-white/10">
              <span class="text-lg font-medium text-slate-900 dark:text-white">{{ room.price }}</span>
              <a href="#book" class="bg-luxury-gold hover:bg-luxury-gold-hover text-white px-6 py-2 rounded-sm text-sm font-medium tracking-wide transition-colors">
                Reserve
              </a>
            </div>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>
