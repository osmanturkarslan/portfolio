<script setup>
import SpaceScene from './components/layout/SpaceScene.vue'
import Hero from './components/sections/Hero.vue'
import ScrollIndicator from './components/layout/ScrollIndicator.vue'
import About from './components/sections/About.vue'
import Contact from './components/sections/Contact.vue'
import EducationCredentials from './components/sections/Education&Credentials.vue'
</script>

<template>
  <!-- Arka plan -->
  <SpaceScene />

  <!-- Ön plan -->
  <div class="relative z-10">
    <Hero />
      <About />
      <EducationCredentials />
      <Contact />
  </div>

  <!-- Scroll Indicator -->
  <ScrollIndicator />
</template>
