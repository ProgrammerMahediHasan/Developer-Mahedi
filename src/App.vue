<template>
  <div
    :class="[
      isDark ? 'bg-[#0f172a] text-[#f8fafc]' : 'bg-[#f9fafb] text-[#020617]',
      'min-h-screen selection:bg-blue-600/30'
    ]"
  >
    <PageLoader :is-loading="isLoading" />

    <Navbar :is-dark="isDark" />

    <main>
      <Hero :is-dark="isDark" />
      <About :is-dark="isDark" />
      <Skills :is-dark="isDark" />
      <Services :is-dark="isDark" />
      <Portfolio :is-dark="isDark" />
      <Experience :is-dark="isDark" />
      <Testimonials :is-dark="isDark" />
      <Contact :is-dark="isDark" />
    </main>

    <Footer :is-dark="isDark" />
  </div>
</template>

<script setup>
import { ref, onMounted, watch } from 'vue'
import PageLoader from './components/layout/PageLoader.vue'
import Navbar from './components/layout/Navbar.vue'
import Footer from './components/layout/Footer.vue'
import Hero from './components/sections/Hero.vue'
import About from './components/sections/About.vue'
import Skills from './components/sections/Skills.vue'
import Services from './components/sections/Services.vue'
import Portfolio from './components/sections/Portfolio.vue'
import Experience from './components/sections/Experience.vue'
import Testimonials from './components/sections/Testimonials.vue'
import Contact from './components/sections/Contact.vue'

const isLoading = ref(true)
const isDark = ref(true)

const applyTheme = () => {
  const root = document.documentElement
  if (isDark.value) {
    root.classList.remove('theme-light')
    localStorage.setItem('theme', 'dark')
  } else {
    root.classList.add('theme-light')
    localStorage.setItem('theme', 'light')
  }
}

onMounted(() => {
  const saved = localStorage.getItem('theme')
  if (saved === 'light') {
    isDark.value = false
  }
  applyTheme()

  setTimeout(() => {
    isLoading.value = false
  }, 1500)
})

</script>
