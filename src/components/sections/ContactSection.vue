<script setup>
</script>

<template>
  <section id="contact" class="py-24 md:py-32 bg-white dark:bg-luxury-surface relative">
    <div class="container mx-auto px-6 md:px-12 flex flex-col lg:flex-row gap-16">
      
      <!-- Contact Info -->
      <div class="w-full lg:w-1/3">
        <p class="text-luxury-gold uppercase tracking-widest text-sm font-semibold mb-4 text-center lg:text-left">Get in Touch</p>
        <h2 class="text-4xl font-serif text-slate-900 dark:text-white font-medium mb-8 text-center lg:text-left">
          Reservations & Inquiries
        </h2>
        
        <form @submit.prevent class="space-y-6 mt-10">
          <div>
            <label class="block text-sm font-medium text-slate-700 dark:text-gray-300 mb-2">Name</label>
            <input type="text" class="w-full px-4 py-3 bg-slate-50 dark:bg-[#020617] border border-slate-200 dark:border-white/10 rounded-sm focus:outline-none focus:border-luxury-gold transition-colors text-slate-900 dark:text-white" placeholder="John Doe" />
          </div>
          <div>
            <label class="block text-sm font-medium text-slate-700 dark:text-gray-300 mb-2">Email</label>
            <input type="email" class="w-full px-4 py-3 bg-slate-50 dark:bg-[#020617] border border-slate-200 dark:border-white/10 rounded-sm focus:outline-none focus:border-luxury-gold transition-colors text-slate-900 dark:text-white" placeholder="john@example.com" />
          </div>
          <div>
            <label class="block text-sm font-medium text-slate-700 dark:text-gray-300 mb-2">Message</label>
            <textarea rows="4" class="w-full px-4 py-3 bg-slate-50 dark:bg-[#020617] border border-slate-200 dark:border-white/10 rounded-sm focus:outline-none focus:border-luxury-gold transition-colors text-slate-900 dark:text-white" placeholder="How can we help you?"></textarea>
          </div>
          <button class="w-full bg-luxury-gold hover:bg-luxury-gold-hover text-white py-4 rounded-sm font-medium tracking-wide uppercase transition-colors">
            Send Message
          </button>
        </form>
      </div>

      <!-- Map Mockup -->
      <div class="w-full lg:w-2/3 h-[500px] lg:h-auto rounded-sm overflow-hidden border border-slate-200 dark:border-white/5 relative">
        <div class="absolute inset-0 bg-slate-200 dark:bg-slate-800 flex items-center justify-center">
            <span class="text-slate-500 font-serif text-xl italic drop-shadow-md z-10 px-8 text-center">Interactive map integration will be placed here.</span>
        </div>
        <img src="https://images.unsplash.com/photo-1524661135-423995f22d0b?q=80&w=2074&auto=format&fit=crop" class="w-full h-full object-cover opacity-50 dark:opacity-20 mix-blend-overlay dark:mix-blend-color-burn" alt="Map View">
      </div>

    </div>
  </section>
</template>
