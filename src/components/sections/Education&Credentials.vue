<template>
  <section class="py-20 px-6 min-h-screen text-white font-sans">
    <div class="max-w-6xl mx-auto">

      <!-- HEADER -->
      <div class="text-center mb-20">
        <h2 class="text-4xl md:text-5xl font-bold mb-6 text-center">Education</h2>
        <p class="max-w-5xl mx-auto font-medium leading-relaxed">
          I began my professional career as an English teacher in Turkey. After relocating to Europe, I decided to pursue a new path in technology, which led me to the world of software development.
        </p>
      </div>

      <!-- 3 COLUMN GRID -->
      <div class="grid md:grid-cols-3 gap-16 items-stretch text-center">

        <!-- UNIVERSITY -->
        <div class="flex flex-col items-center h-full">
        <!-- <div class="flex flex-col items-center h-full h-full bg-black/30 border border-white/15 backdrop-blur-md p-6 rounded-2xl shadow-[0_12px_30px_rgba(56,189,248,0.22)]"> -->
          
          <div class="relative mb-8 flex justify-center">
            <div class="w-56 h-56 rounded-full flex items-center justify-center 
                        transition duration-500 hover:scale-105">
              <img 
                src="../../assets/uludag-üni-logo.png"
                class="w-50 h-50 object-contain rounded-full"
                alt="University"
              />
            </div>
          </div>

          <h3 class="text-2xl font-bold mb-3 text-cyan-200">University</h3>

          <p class="text-sm font-medium max-w-xs mx-auto mb-6 text-slate-300 leading-relaxed">
            I graduated from Uludag University with the degree of 
            Bachelor of Arts (BA) in English Language Teacher Education 
            - Bursa / Turkey in 2014.
          </p>

          <div class="flex gap-3 mt-auto">
            <button @click="openModal('diploma')" class="glass-btn">
              Diploma
            </button>
            <button @click="openModal('diplomaEu')" class="glass-btn">
              Diploma-EU
            </button>
          </div>
        </div>

        <!-- BOOTCAMP -->
        <div class="flex flex-col items-center">

          <div class="relative mb-8 flex justify-center">
            <div class="w-56 h-56 rounded-full flex items-center justify-center 
                        transition duration-500 hover:scale-105">

                        <img 
                src="../../assets/techpro-logo.png"
                class="w-50 h-50 object-contain rounded-full"
                alt="Bootcamp"
              />
              
            </div>
          </div>

          <h3 class="text-2xl font-bold mb-3 text-cyan-200">Bootcamp</h3>

          <p class="text-sm font-medium max-w-xs mx-auto mb-6 text-slate-300 leading-relaxed">
            I completed a Full-Stack Java Developer Bootcamp at 
            Techpro Education – Professional Development Activities 
            - Florida / USA in 2021.
          </p>

          <div class="flex gap-3 mt-auto">
            <button @click="openModal('certificate')" class="glass-btn">
              Certificate
            </button>
          </div>
        </div>

        <!-- RESUME -->
        <div class="flex flex-col items-center">

          <div class="relative mb-8 flex justify-center">
            <div class="w-56 h-56  
                        flex flex-col items-center justify-center 
                        
                        transition duration-500 hover:scale-105">
              <img 
                src="../../assets/my-resume.jpg"
                class="w-50 h-50 object-contain"
                alt="Resume"
              />
            </div>
          </div>

          <h3 class="text-2xl font-bold mb-3 text-cyan-200">Resume</h3>

          <p class="text-sm font-medium max-w-xs mx-auto mb-6 text-slate-300 leading-relaxed">
            I am ready to take part in the professional IT market.
          </p>

          <div class="flex gap-3 mt-auto">
            <button @click="openModal('resume')" class="glass-btn px-8">
              Resume
            </button>
          </div>
        </div>

      </div>
    </div>

    <!-- MODAL -->
    <Transition name="fade">
      <div 
        v-if="isOpen" 
        class="fixed inset-0 bg-black/60 backdrop-blur-md 
               flex items-center justify-center z-[100] p-6"
        @click.self="closeModal"
      >
        <div class="bg-white w-full max-w-5xl h-[85vh] 
                    rounded-3xl relative shadow-2xl 
                    overflow-hidden border border-white/20">
          <button 
            @click="closeModal" 
            class="absolute top-4 right-6 text-gray-500 
                   hover:text-black text-2xl z-50">
            ✕
          </button>
          <iframe 
            :src="currentFile" 
            class="w-full h-full border-none pt-12">
          </iframe>
        </div>
      </div>
    </Transition>

  </section>
</template>

<script setup>
import { ref } from 'vue'
import diplomaPdf from '/src/assets/diploma.pdf'
import diplomaEuPdf from '/src/assets/diploma-eu.pdf'
import certificatePdf from '/src/assets/certificate.pdf'
import resumePdf from '/src/assets/resume.pdf'

const isOpen = ref(false)
const currentFile = ref('')

const fileMap = {
  diploma: diplomaPdf,
  diplomaEu: diplomaEuPdf,
  certificate: certificatePdf,
  resume: resumePdf,
}

const openModal = (fileKey) => {
  currentFile.value = fileMap[fileKey]
  isOpen.value = true
}

const closeModal = () => {
  isOpen.value = false
}
</script>

<style scoped>
.glass-btn {
  background: rgba(15, 23, 42, 0.55);
  backdrop-filter: blur(6px);
  border: 1px solid rgba(100, 216, 255, 0.45);
  padding: 10px 20px;
  border-radius: 9999px;
  color: #e0f2fe;
  font-weight: 700;
  font-size: 0.9rem;
  letter-spacing: 0.04em;
  font-variant-ligatures: contextual;
  text-transform: uppercase;
  box-shadow: 0 0 18px rgba(56, 189, 248, 0.35);
  transition: all 0.25s ease;
  text-shadow: 0 1px 2px rgba(8, 145, 178, 0.6);
}

.glass-btn:hover {
  background: rgba(56, 189, 248, 0.95);
  color: #0f172a;
  transform: translateY(-2px) scale(1.02);
  box-shadow: 0 8px 26px rgba(56, 189, 248, 0.45);
}

.fade-enter-active, .fade-leave-active {
  transition: opacity 0.4s ease;
}
.fade-enter-from, .fade-leave-to {
  opacity: 0;
}

h3 {
  letter-spacing: 0.03em;
}

img{
    width: 200px;
}


</style>