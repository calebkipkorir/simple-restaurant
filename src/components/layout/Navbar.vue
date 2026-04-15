<script setup>
import { ref, onMounted, onUnmounted } from 'vue'
import { useDark, useToggle, useWindowScroll } from '@vueuse/core'
import { Menu, X, Moon, Sun, Hotel } from 'lucide-vue-next'

const isDark = useDark()
const toggleDark = useToggle(isDark)

const { y } = useWindowScroll()
const isMenuOpen = ref(false)

const toggleMenu = () => {
  isMenuOpen.value = !isMenuOpen.value
}

const navLinks = [
  { name: 'About', href: '/#about' },
  { name: 'Rooms & Suites', href: '/rooms' },
  { name: 'Dining', href: '/dining' },
  { name: 'Wellness & Spa', href: '/spa' },
  { name: 'Gallery', href: '/#gallery' },
  { name: 'Contact', href: '/#contact' },
]
</script>

<template>
  <header 
    :class="[
      'fixed top-0 w-full z-50 lux-transition border-b border-transparent',
      y > 50 ? 'bg-white/80 dark:bg-luxury-dark/80 backdrop-blur-md shadow-sm dark:border-white/10 py-3' : 'bg-transparent py-5'
    ]"
  >
    <div class="container mx-auto px-6 md:px-12 flex items-center justify-between">
      
      <!-- Brand Logo -->
      <router-link to="/" class="flex items-center gap-2 group outline-none">
        <div class="text-luxury-gold">
          <Hotel class="w-8 h-8 group-hover:-rotate-12 transition-transform duration-300" />
        </div>
        <span class="font-serif text-2xl font-bold tracking-wider text-slate-900 dark:text-white group-hover:text-luxury-gold transition-colors">
          LUMINA
        </span>
      </router-link>

      <!-- Desktop Navigation -->
      <nav class="hidden md:flex items-center gap-8">
        <router-link 
          v-for="link in navLinks" 
          :key="link.name" 
          :to="link.href"
          class="font-medium text-sm text-slate-800 dark:text-gray-300 hover:text-luxury-gold dark:hover:text-luxury-gold transition-colors"
        >
          {{ link.name }}
        </router-link>
        
        <button 
          @click="toggleDark()" 
          class="p-2 rounded-full hover:bg-slate-100 dark:hover:bg-white/10 transition-colors"
          aria-label="Toggle Dark Mode"
        >
          <Sun v-if="isDark" class="w-5 h-5 text-luxury-gold" />
          <Moon v-else class="w-5 h-5 text-slate-700" />
        </button>

        <a href="#book" class="bg-luxury-gold hover:bg-luxury-gold-hover text-white px-6 py-2 rounded-sm font-medium tracking-wide transition-colors">
          Book Now
        </a>
      </nav>

      <!-- Mobile Menu Toggle -->
      <div class="flex items-center gap-4 md:hidden">
        <button 
          @click="toggleDark()" 
          class="p-2 rounded-full hover:bg-slate-100 dark:hover:bg-white/10 transition-colors"
          aria-label="Toggle Dark Mode"
        >
          <Sun v-if="isDark" class="w-5 h-5 text-luxury-gold" />
          <Moon v-else class="w-5 h-5 text-slate-700" />
        </button>
        <button @click="toggleMenu" class="text-slate-900 dark:text-white p-2">
          <X v-if="isMenuOpen" class="w-6 h-6" />
          <Menu v-else class="w-6 h-6" />
        </button>
      </div>

    </div>

    <!-- Mobile Navigation Menu -->
    <div 
      v-show="isMenuOpen"
      class="absolute top-full left-0 w-full bg-white dark:bg-luxury-surface border-b dark:border-white/10 shadow-lg py-4 px-6 md:hidden flex flex-col gap-4"
    >
      <router-link 
        v-for="link in navLinks" 
        :key="link.name" 
        :to="link.href"
        @click="isMenuOpen = false"
        class="font-medium text-lg text-slate-800 dark:text-gray-300 hover:text-luxury-gold transition-colors py-2 border-b dark:border-white/5 last:border-0"
      >
        {{ link.name }}
      </router-link>
      <a href="#book" class="bg-luxury-gold text-white px-6 py-3 rounded-sm font-medium tracking-wide text-center mt-2" @click="isMenuOpen = false">
        Book Now
      </a>
    </div>
  </header>
</template>
