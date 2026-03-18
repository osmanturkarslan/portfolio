<script setup>
import * as THREE from 'three'
import { ref, onMounted } from 'vue'

const cameraRef = ref(null)

const mouse = { x: 0, y: 0 }
const targetRotation = { x: 0, y: 0 }

const textureLoader = new THREE.TextureLoader()

// Nebula texture
const nebulaTexture = textureLoader.load(
  '/src/assets/nebula31.jpg'
)
const planeWidth = 4000
const planeHeight = 2000

nebulaTexture.minFilter = THREE.LinearFilter
nebulaTexture.magFilter = THREE.LinearFilter
nebulaTexture.generateMipmaps = true
nebulaTexture.anisotropy = 4

// Star texture
// const starTexture = textureLoader.load('/star.png')
// const starTexture = textureLoader.load('/src/assets/star.png')
const starTexture = createStarTexture()

// Dinamik yıldız dokusu oluşturma
function createStarTexture() {
  const size = 512
  const canvas = document.createElement('canvas')
  canvas.width = size
  canvas.height = size
  const ctx = canvas.getContext('2d')

  const center = size / 2

  // Küçük yoğun çekirdek
  const core = ctx.createRadialGradient(
    center, center, 0,
    center, center, size * 0.08
  )
  core.addColorStop(0, 'white')
  core.addColorStop(1, 'transparent')

  ctx.fillStyle = core
  ctx.fillRect(0, 0, size, size)

  // Yumuşak halo (küçük)
  const halo = ctx.createRadialGradient(
    center, center, 0,
    center, center, size * 0.22
  )
  halo.addColorStop(0, 'rgba(255,255,255,0.4)')
  halo.addColorStop(1, 'transparent')

  ctx.fillStyle = halo
  ctx.fillRect(0, 0, size, size)

  // Yumuşak spike'lar (gradient koni gibi)
  const spikes = 4
  const radius = size * 0.45

  ctx.translate(center, center)

  for (let i = 0; i < spikes; i++) {
    const angle = (Math.PI * 2 / spikes) * i

    const grad = ctx.createLinearGradient(
      0, 0,
      Math.cos(angle) * radius,
      Math.sin(angle) * radius
    )

    grad.addColorStop(0, 'rgba(255,255,255,0.8)')
    grad.addColorStop(1, 'transparent')

    ctx.strokeStyle = grad
    ctx.lineWidth = 8
    ctx.lineCap = 'round'

    ctx.beginPath()
    ctx.moveTo(0, 0)
    ctx.lineTo(
      Math.cos(angle) * radius,
      Math.sin(angle) * radius
    )
    ctx.stroke()
  }

  const texture = new THREE.CanvasTexture(canvas)
  texture.needsUpdate = true
  return texture
}

// scrool speed
let speedMultiplier = 1
let scrollBoost = 0

// Yıldız katmanı
function createStars(count, spread, size, baseOpacity) {
  const geometry = new THREE.BufferGeometry()
  const positions = new Float32Array(count * 3)

  for (let i = 0; i < count * 3; i += 3) {
    positions[i] = (Math.random() - 0.5) * spread
    positions[i + 1] = (Math.random() - 0.5) * spread
    positions[i + 2] = -Math.random() * spread - 5
  }

  geometry.setAttribute(
    'position',
    new THREE.BufferAttribute(positions, 3)
  )

  const material = new THREE.PointsMaterial({
    map: starTexture,
    transparent: true,
    depthWrite: false,
    blending: THREE.AdditiveBlending,
    size,
    sizeAttenuation: true,
    opacity: baseOpacity,
    color: 0xe0e6ff
  })

  return { geometry, material, baseOpacity }
}

const starsNear = createStars(800, 60, 0.5, 0.9)
const starsMid = createStars(1600, 80, 0.4, 0.6)
const starsFar = createStars(2400, 100, 0.3, 0.3)

function moveStars(stars, speed) {
  const pos = stars.geometry.attributes.position

  for (let i = 0; i < pos.count; i++) {
    let z = pos.getZ(i)
    z += speed
    if (z > 10) z = -80
    pos.setZ(i, z)
  }

  pos.needsUpdate = true
}

onMounted(() => {
  window.addEventListener('mousemove', (e) => {
    mouse.x = (e.clientX / window.innerWidth - 0.5) * 2
    mouse.y = (e.clientY / window.innerHeight - 0.5) * 2

    targetRotation.y = mouse.x * 0.12
    targetRotation.x = mouse.y * 0.08
  })

let lastScrollY = window.scrollY

window.addEventListener('scroll', () => {
  const currentScrollY = window.scrollY
  const delta = Math.abs(currentScrollY - lastScrollY)

  scrollBoost += delta * 0.02

  lastScrollY = currentScrollY
})

  const clock = new THREE.Clock()

  function animate() {
    requestAnimationFrame(animate)

    const t = clock.getElapsedTime()
    const breath = Math.sin(t * 0.45)

    starsNear.material.opacity =
      starsNear.baseOpacity + breath * 0.04

    starsMid.material.opacity =
      starsMid.baseOpacity + Math.sin(t * 0.45 + 1) * 0.03

    starsFar.material.opacity =
      starsFar.baseOpacity + Math.sin(t * 0.45 + 2) * 0.02

    starsNear.material.size = 0.5 + breath * 0.1
    starsMid.material.size = 0.4 + breath * 0.08
    starsFar.material.size = 0.3 + breath * 0.06

    if (cameraRef.value) {
      cameraRef.value.rotation.y +=
        (targetRotation.y - cameraRef.value.rotation.y) * 0.05

      cameraRef.value.rotation.x +=
        (targetRotation.x - cameraRef.value.rotation.x) * 0.05
    }

    scrollBoost *= 0.99
    speedMultiplier = 1 + scrollBoost

    moveStars(starsNear, 0.008 * speedMultiplier)
    moveStars(starsMid, 0.004 * speedMultiplier)
    moveStars(starsFar, 0.001 * speedMultiplier)

  }
  animate()


  


})




</script>

<template>
  <TresCanvas clear-color="#000000" window-size>
    <TresPerspectiveCamera ref="cameraRef" :position="[0, 0, 10]" :fov="65" />

    <TresAmbientLight :intensity="1" />

    <!-- Nebula Plane -->
    <TresMesh :position="[0, 0, -850]">
      <TresPlaneGeometry :args="[planeWidth, planeHeight]" />
      <TresMeshBasicMaterial :map="nebulaTexture" transparent :opacity="0.3" />
    </TresMesh>

    <!-- Stars -->
    <TresPoints :geometry="starsFar.geometry" :material="starsFar.material" />
    <TresPoints :geometry="starsMid.geometry" :material="starsMid.material" />
    <TresPoints :geometry="starsNear.geometry" :material="starsNear.material" />
  </TresCanvas>
</template>

<style scoped>
canvas {
  position: fixed;
  inset: 0;
  z-index: -1;
  pointer-events: none;
}
</style>
