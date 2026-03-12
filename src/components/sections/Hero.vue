<template>
  <section class="relative min-h-screen flex items-center justify-center px-6 py-16">
    <div class="max-w-6xl w-full grid grid-cols-1 lg:grid-cols-2 gap-8 items-center">
      <div ref="hero" class="space-y-6 text-left">
        <p class="text-sm uppercase tracking-widest text-cyan-300/80">Platform Developer</p>
        <h1 class="text-4xl md:text-6xl font-bold leading-tight text-white">
          Osman <span class="text-cyan-300">Türkarslan</span>
        </h1>
        <p class="text-lg md:text-xl text-slate-200 max-w-xl">
         Informatics student passionate about platform engineering, automation, and modern software technologies.
        </p>

      </div>

      <div class="relative flex justify-center lg:justify-end">
        <div class="relative w-[620px] max-w-full">
          <img src="/src/assets/portre2.png" alt="Osman Türkarslan" class="w-full h-auto" />
        </div>
      </div>
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

