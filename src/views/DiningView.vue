<script setup>
import { onMounted, ref } from 'vue'
import { gsap } from 'gsap'
import { ScrollTrigger } from 'gsap/ScrollTrigger'

const headerRef = ref(null)
const menuRef = ref(null)

const starters = [
  { name: 'Oysters Rockefeller', description: 'Freshly shucked oysters, spinach, herbs, butter, breadcrumbs', price: '$28' },
  { name: 'Wagyu Beef Carpaccio', description: 'Truffle aioli, shaved parmesan, wild arugula, capers', price: '$34' },
  { name: 'Lobster Bisque', description: 'Maine lobster, cognac cream, tarragon, puff pastry', price: '$22' }
]

const mains = [
  { name: 'Pan-Seared Halibut', description: 'Cauliflower purée, brown butter caper sauce, asparagus', price: '$48' },
  { name: 'Dry-Aged Ribeye', description: 'Pommes frites, roasted garlic, bone marrow butter', price: '$65' },
  { name: 'Truffle Risotto', description: 'Arborio rice, seasonal mushrooms, shaved black truffle, parmesan', price: '$42' }
]

const desserts = [
  { name: 'Valrhona Chocolate Soufflé', description: 'Grand Marnier crème anglaise, vanilla bean ice cream', price: '$18' },
  { name: 'Lemon Basil Tart', description: 'Toasted meringue, raspberry coulis', price: '$16' }
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

  // Menu items animation
  gsap.from('.menu-item', {
    y: 30,
    opacity: 0,
    duration: 0.8,
    stagger: 0.1,
    ease: "power2.out",
    scrollTrigger: {
      trigger: menuRef.value,
      start: "top 80%",
    }
  })
})
</script>

<template>
  <div class="min-h-screen pt-24 pb-12 bg-slate-50 dark:bg-[#080d1e]">
    <!-- Hero Section for Dining -->
    <section class="relative h-[60vh] w-full flex items-center justify-center overflow-hidden">
      <div 
        class="absolute inset-0 w-full h-full bg-cover bg-center"
        style="background-image: url('https://images.unsplash.com/photo-1414235077428-338989a2e8c0?auto=format&fit=crop&w=1920&q=80');"
      ></div>
      <div class="absolute inset-0 bg-black/50"></div>
      
      <div ref="headerRef" class="relative z-10 text-center px-4">
        <p class="text-luxury-gold uppercase tracking-[0.2em] text-sm md:text-base font-semibold mb-4">
          Culinary Excellence
        </p>
        <h1 class="text-4xl md:text-6xl font-serif text-white font-medium drop-shadow-lg">
          A Symphony of Taste
        </h1>
      </div>
    </section>

    <!-- Menu Content -->
    <section class="container mx-auto px-6 md:px-12 py-20 max-w-4xl" ref="menuRef">
      <div class="text-center mb-16">
        <h2 class="text-3xl font-serif text-slate-900 dark:text-white mb-6">Our Signature Menu</h2>
        <div class="h-px w-16 bg-luxury-gold mx-auto"></div>
        <p class="mt-8 text-slate-600 dark:text-gray-400 leading-relaxed">
          Crafted by our Michelin-starred culinary team, our menu celebrates seasonal ingredients, blending classic techniques with modern innovation to deliver an unforgettable dining experience.
        </p>
      </div>

      <!-- Starters -->
      <div class="mb-16">
        <h3 class="text-2xl font-serif text-luxury-gold mb-8 text-center uppercase tracking-widest">Starters</h3>
        <div class="space-y-8">
          <div v-for="item in starters" :key="item.name" class="menu-item flex flex-col md:flex-row justify-between items-baseline gap-4 border-b border-slate-200 dark:border-white/10 pb-4">
            <div class="flex-grow">
              <h4 class="text-xl font-serif text-slate-900 dark:text-gray-100">{{ item.name }}</h4>
              <p class="text-sm text-slate-500 dark:text-gray-400 mt-1 italic">{{ item.description }}</p>
            </div>
            <div class="text-luxury-gold font-medium">{{ item.price }}</div>
          </div>
        </div>
      </div>

      <!-- Mains -->
      <div class="mb-16">
        <h3 class="text-2xl font-serif text-luxury-gold mb-8 text-center uppercase tracking-widest">Mains</h3>
        <div class="space-y-8">
          <div v-for="item in mains" :key="item.name" class="menu-item flex flex-col md:flex-row justify-between items-baseline gap-4 border-b border-slate-200 dark:border-white/10 pb-4">
            <div class="flex-grow">
              <h4 class="text-xl font-serif text-slate-900 dark:text-gray-100">{{ item.name }}</h4>
              <p class="text-sm text-slate-500 dark:text-gray-400 mt-1 italic">{{ item.description }}</p>
            </div>
            <div class="text-luxury-gold font-medium">{{ item.price }}</div>
          </div>
        </div>
      </div>

      <!-- Desserts -->
      <div>
        <h3 class="text-2xl font-serif text-luxury-gold mb-8 text-center uppercase tracking-widest">Desserts</h3>
        <div class="space-y-8">
          <div v-for="item in desserts" :key="item.name" class="menu-item flex flex-col md:flex-row justify-between items-baseline gap-4 border-b border-slate-200 dark:border-white/10 pb-4">
            <div class="flex-grow">
              <h4 class="text-xl font-serif text-slate-900 dark:text-gray-100">{{ item.name }}</h4>
              <p class="text-sm text-slate-500 dark:text-gray-400 mt-1 italic">{{ item.description }}</p>
            </div>
            <div class="text-luxury-gold font-medium">{{ item.price }}</div>
          </div>
        </div>
      </div>

    </section>
  </div>
</template>
