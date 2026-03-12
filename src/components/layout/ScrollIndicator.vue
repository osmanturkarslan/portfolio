<script setup>
import { ref, onMounted, onUnmounted, computed } from 'vue'

const scrollProgress = ref(0)
const isVisible = ref(false)

const updateScroll = () => {
  const scrollTop = window.scrollY
  const docHeight =
    document.documentElement.scrollHeight - window.innerHeight

  if (docHeight > 0) {
    scrollProgress.value = (scrollTop / docHeight) * 100
  }

  isVisible.value = scrollTop > 50
}

const scrollToTop = () => {
  window.scrollTo({
    top: 0,
    behavior: 'smooth'
  })
}

onMounted(() => {
  window.addEventListener('scroll', updateScroll)
})

onUnmounted(() => {
  window.removeEventListener('scroll', updateScroll)
})
</script>

<template>
  <div
    class="scroll-indicator"
    :class="{ visible: isVisible }"
    @click="scrollToTop"
  >
    <div
      class="scroll-bar"
      :style="{ width: scrollProgress + '%' }"
    ></div>
  </div>
</template>

<style scoped>
.scroll-indicator {
  position: fixed;
  bottom: 40px;
  left: 50%;
  transform: translateX(-50%);
  width: 220px;
  height: 6px;
  background: rgba(255,255,255,0.06);
  border-radius: 10px;
  z-index: 20;
  overflow: hidden;
  cursor: pointer;

  opacity: 0;
  transition: opacity 0.4s ease;
}

.scroll-indicator.visible {
  opacity: 1;
}

.scroll-bar {
  height: 100%;
  width: 0%;
  background: linear-gradient(90deg, #6f8cff, #a855f7);
  box-shadow:
    0 0 8px rgba(111,140,255,0.7),
    0 0 16px rgba(168,85,247,0.6);
  border-radius: 10px;
  transition: width 0.15s ease-out;
}

.scroll-indicator:hover .scroll-bar {
  box-shadow:
    0 0 12px rgba(111,140,255,0.9),
    0 0 24px rgba(168,85,247,0.8);
}
</style>