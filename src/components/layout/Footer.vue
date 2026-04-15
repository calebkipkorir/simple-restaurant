<script setup>
import { Hotel, Facebook, Twitter, Instagram, MapPin, Phone, Mail } from 'lucide-vue-next'
</script>

<template>
  <footer class="bg-slate-50 dark:bg-luxury-surface border-t border-slate-200 dark:border-white/10 py-16">
    <div class="container mx-auto px-6 md:px-12 grid grid-cols-1 md:grid-cols-4 gap-12">
      
      <!-- Brand & Info -->
      <div class="col-span-1 md:col-span-1">
        <a href="#" class="flex items-center gap-2 mb-6 group outline-none">
          <div class="text-luxury-gold">
            <Hotel class="w-8 h-8 group-hover:-rotate-12 transition-transform duration-300" />
          </div>
          <span class="font-serif text-2xl font-bold tracking-wider text-slate-900 dark:text-white">
            LUMINA
          </span>
        </a>
        <p class="text-slate-600 dark:text-gray-400 text-sm leading-relaxed mb-6">
          Experience unrivaled luxury and impeccable service at Lumina. Your perfect escape from the ordinary, where every detail is crafted for your comfort.
        </p>
        <div class="flex gap-4">
          <a href="#" class="p-2 rounded-full border border-slate-200 dark:border-white/10 text-slate-600 dark:text-gray-400 hover:text-luxury-gold dark:hover:text-luxury-gold transition-colors">
            <Facebook class="w-4 h-4" />
          </a>
          <a href="#" class="p-2 rounded-full border border-slate-200 dark:border-white/10 text-slate-600 dark:text-gray-400 hover:text-luxury-gold dark:hover:text-luxury-gold transition-colors">
            <Twitter class="w-4 h-4" />
          </a>
          <a href="#" class="p-2 rounded-full border border-slate-200 dark:border-white/10 text-slate-600 dark:text-gray-400 hover:text-luxury-gold dark:hover:text-luxury-gold transition-colors">
            <Instagram class="w-4 h-4" />
          </a>
        </div>
      </div>

      <!-- Quick Links -->
      <div>
        <h4 class="font-serif text-lg font-semibold text-slate-900 dark:text-white mb-6">Quick Links</h4>
        <ul class="space-y-3">
          <li v-for="link in ['About Us', 'Rooms & Suites', 'Dining', 'Spa & Wellness', 'Gallery', 'Offers']" :key="link">
            <a href="#" class="text-slate-600 dark:text-gray-400 hover:text-luxury-gold dark:hover:text-luxury-gold text-sm transition-colors">
              {{ link }}
            </a>
          </li>
        </ul>
      </div>

      <!-- Legal -->
      <div>
        <h4 class="font-serif text-lg font-semibold text-slate-900 dark:text-white mb-6">Legal</h4>
        <ul class="space-y-3">
          <li v-for="link in ['Terms & Conditions', 'Privacy Policy', 'Cookie Policy', 'Cancellation Policy']" :key="link">
            <a href="#" class="text-slate-600 dark:text-gray-400 hover:text-luxury-gold dark:hover:text-luxury-gold text-sm transition-colors">
              {{ link }}
            </a>
          </li>
        </ul>
      </div>

      <!-- Contact -->
      <div>
        <h4 class="font-serif text-lg font-semibold text-slate-900 dark:text-white mb-6">Contact Us</h4>
        <ul class="space-y-4">
          <li class="flex items-start gap-3 text-slate-600 dark:text-gray-400 text-sm">
            <MapPin class="w-5 h-5 text-luxury-gold shrink-0 mt-0.5" />
            <span>123 Luxury Avenue, Coastal District, City 10010</span>
          </li>
          <li class="flex items-center gap-3 text-slate-600 dark:text-gray-400 text-sm">
            <Phone class="w-5 h-5 text-luxury-gold shrink-0" />
            <span>+1 (555) 123-4567</span>
          </li>
          <li class="flex items-center gap-3 text-slate-600 dark:text-gray-400 text-sm">
            <Mail class="w-5 h-5 text-luxury-gold shrink-0" />
            <span>reservations@lumina-hotel.com</span>
          </li>
        </ul>
      </div>

    </div>
    
    <div class="container mx-auto px-6 md:px-12 mt-16 pt-8 border-t border-slate-200 dark:border-white/10 text-center flex flex-col md:flex-row justify-between items-center gap-4">
      <p class="text-slate-500 dark:text-gray-500 text-sm">
        &copy; {{ new Date().getFullYear() }} Lumina Hotel & Spa. All rights reserved.
      </p>
    </div>
  </footer>
</template>
