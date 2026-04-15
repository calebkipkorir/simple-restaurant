<script setup>
import { ref, onMounted, onUnmounted } from 'vue'
import { gsap } from 'gsap'
import { ScrollTrigger } from 'gsap/ScrollTrigger'
import { ChevronLeft, ChevronRight, Quote } from 'lucide-vue-next'

const sectionRef = ref(null)
const carouselRef = ref(null)
const currentIndex = ref(0)

const testimonials = [
  {
    quote: "An absolute masterpiece of hospitality. The attention to detail from the moment we arrived until checkout was nothing short of perfection.",
    author: "Elena R.",
    role: "Global Traveler"
  },
  {
    quote: "The culinary experience alone is worth the trip. Waking up to panoramic city views in the impeccably designed suite was unforgettable.",
    author: "Marcus T.",
    role: "Architecture Digest"
  },
  {
    quote: "A true sanctuary in the bustling city. The spa treatments reset my entirely, and the concierge preemptively knew exactly what I needed.",
    author: "Sarah J.",
    role: "Business Executive"
  }
]

const nextTestimonial = () => {
  currentIndex.value = (currentIndex.value + 1) % testimonials.length
}

const prevTestimonial = () => {
  currentIndex.value = (currentIndex.value - 1 + testimonials.length) % testimonials.length
}

let autoplayInterval

const startAutoplay = () => {
  autoplayInterval = setInterval(() => {
    nextTestimonial()
  }, 5000)
}

const stopAutoplay = () => {
  if (autoplayInterval) {
    clearInterval(autoplayInterval)
  }
}

onMounted(() => {
  startAutoplay()

  gsap.registerPlugin(ScrollTrigger)

  gsap.from(sectionRef.value, {
    opacity: 0,
    y: 30,
    duration: 1,
    ease: "power2.out",
    scrollTrigger: {
      trigger: sectionRef.value,
      start: "top 75%",
    }
  })
})

onUnmounted(() => {
  stopAutoplay()
})
</script>

<template>
  <section ref="sectionRef" class="py-24 md:py-32 bg-slate-50 dark:bg-luxury-dark overflow-hidden">
    <div class="container mx-auto px-6 md:px-12">
      
      <div class="max-w-4xl mx-auto text-center relative" @mouseenter="stopAutoplay" @mouseleave="startAutoplay">
        <Quote class="w-16 h-16 text-luxury-gold/20 mx-auto mb-8 absolute -top-10 left-1/2 -translate-x-1/2" />
        
        <div class="relative h-[350px] sm:h-[300px] md:h-[250px] overflow-hidden" ref="carouselRef">
          <transition-group 
            name="slide" 
            tag="div"
            class="relative w-full h-full flex items-center justify-center"
          >
            <div 
              v-for="(t, index) in testimonials" 
              :key="index"
              v-show="index === currentIndex"
              class="absolute inset-0 flex flex-col items-center justify-center w-full px-4"
            >
              <p class="text-xl md:text-3xl font-serif text-slate-900 dark:text-white leading-relaxed mb-8 italic">
                "{{ t.quote }}"
              </p>
              <div>
                <p class="text-luxury-gold font-semibold uppercase tracking-widest text-sm">{{ t.author }}</p>
                <p class="text-slate-500 dark:text-gray-500 text-sm mt-1 mb-6">{{ t.role }}</p>
              </div>
            </div>
          </transition-group>
        </div>

        <div class="flex items-center justify-center gap-4 mt-6">
          <button @click="prevTestimonial" class="p-3 rounded-full border border-slate-200 dark:border-white/10 hover:bg-luxury-gold hover:border-luxury-gold text-slate-700 dark:text-white transition-colors group">
            <ChevronLeft class="w-5 h-5 group-hover:text-white" />
          </button>
          
          <div class="flex gap-2 mx-4">
            <button 
              v-for="(_, idx) in testimonials" 
              :key="idx" 
              @click="currentIndex = idx"
              class="w-2 h-2 rounded-full transition-all duration-300"
              :class="idx === currentIndex ? 'bg-luxury-gold w-6' : 'bg-slate-300 dark:bg-white/20'"
              aria-label="Go to testimonial"
            ></button>
          </div>

          <button @click="nextTestimonial" class="p-3 rounded-full border border-slate-200 dark:border-white/10 hover:bg-luxury-gold hover:border-luxury-gold text-slate-700 dark:text-white transition-colors group">
            <ChevronRight class="w-5 h-5 group-hover:text-white" />
          </button>
        </div>

      </div>
    </div>
  </section>
</template>

<style scoped>
.slide-enter-active,
.slide-leave-active {
  transition: all 0.5s ease;
}
.slide-enter-from {
  opacity: 0;
  transform: translateX(30px);
}
.slide-leave-to {
  opacity: 0;
  transform: translateX(-30px);
}
.slide-leave-active {
  position: absolute;
}
</style
