<template>
  <footer class="text-center text-sm text-slate-300 py-6 mt-8 border-t border-white/10">
    <p class="text-gray-200">© {{ year }} Osman Türkarslan. All rights reserved.</p>
  </footer>
</template>

<script setup>
const year = new Date().getFullYear()
</script>
