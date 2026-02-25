<template>
  <footer class="py-12" :class="isDark ? 'bg-[#0f172a] border-t border-gray-800' : 'bg-white border-t border-slate-200'">
    <div class="container mx-auto px-6">
      <div class="flex flex-col md:flex-row justify-between items-center">
        <div class="mb-8 md:mb-0">
          <a href="#" class="text-2xl font-bold tracking-wider" :class="isDark ? 'text-white' : 'text-slate-900'">
            Developer <span class="text-blue-500">Mahedi</span>
          </a>
          <p class="mt-4 max-w-xs" :class="isDark ? 'text-gray-500' : 'text-slate-600'">
            Building digital products, brands, and experiences with passion and precision.
          </p>
        </div>

        <div class="flex space-x-6 mb-8 md:mb-0">
          <a
            v-for="social in socials"
            :key="social.name"
            :href="social.link"
            target="_blank"
            class="w-10 h-10 rounded-full flex items-center justify-center transition-all duration-300"
            :class="isDark ? 'bg-[#1e293b] text-gray-400 hover:bg-blue-600 hover:text-white' : 'bg-slate-100 text-slate-600 hover:bg-blue-600 hover:text-white'"
          >
            <component :is="social.icon" class="w-5 h-5" />
          </a>
        </div>

        <div class="text-sm" :class="isDark ? 'text-gray-500' : 'text-slate-600'">
          © {{ new Date().getFullYear() }} Mahedi Hasan. All rights reserved.
        </div>
      </div>
      
      <!-- Back to Top -->
      <button 
        v-show="showBackToTop"
        @click="scrollToTop"
        class="fixed bottom-8 right-8 w-12 h-12 bg-blue-600 text-white rounded-full flex items-center justify-center shadow-lg hover:bg-blue-700 transition-all transform hover:-translate-y-2 z-50"
      >
        <ArrowUp class="w-6 h-6" />
      </button>
    </div>
  </footer>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'
import { Linkedin, Github, Facebook, Instagram, ArrowUp } from 'lucide-vue-next'
const props = defineProps({ isDark: Boolean })

const showBackToTop = ref(false)

const socials = [
  { name: 'LinkedIn', link: 'https://www.linkedin.com/in/mahedihasan8/', icon: Linkedin },
  { name: 'GitHub', link: 'https://github.com/ProgrammerMahediHasan', icon: Github },
  { name: 'Facebook', link: 'https://www.facebook.com/MahediHasanAbir8/', icon: Facebook },
  { name: 'Instagram', link: 'https://www.instagram.com/mahedi_hasan_abir8/', icon: Instagram }
]

const handleScroll = () => {
  showBackToTop.value = window.scrollY > 500
}

const scrollToTop = () => {
  window.scrollTo({ top: 0, behavior: 'smooth' })
}

onMounted(() => {
  window.addEventListener('scroll', handleScroll)
})

onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll)
})
</script>
