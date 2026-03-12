<template>
  <section class="relative min-h-screen flex items-center justify-center px-6 ">
    <div ref="hero" class="max-w-3xl text-center">
      <p class="text-sm uppercase tracking-widest text-gray-400 mb-4">
        Plattform Developer
      </p>

      <h1 class="text-5xl md:text-7xl font-bold leading-tight mb-6">
        Osman
        <span class="text-gray-300">Türkarslan</span>
      </h1>

      <p class="text-lg text-gray-300 max-w-xl mx-auto">
        Modern, clean and performant web interfaces with Vue.
      </p>
    </div>
    
  </section>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import gsap from 'gsap'

const hero = ref(null)

onMounted(() => {
  gsap.from(hero.value.children, {
    opacity: 0,
    y: 20,
    duration: 0.8,
    stagger: 0.15,
    ease: 'power2.out'
  })
})


</script>


<!--
<section class="relative min-h-screen flex items-center justify-center px-6">
  <div class="absolute inset-0 bg-gradient-to-b from-black/30 via-transparent to-black/30"></div>
  <div class="relative z-10">
     // hero content
  </div>
</section>
-->

