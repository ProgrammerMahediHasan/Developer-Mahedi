<template>
  <section id="home" class="min-height-screen flex items-center pt-20 relative overflow-hidden">
    <div class="absolute inset-0 -z-10 aurora opacity-80"></div>
    <div class="container mx-auto px-6 grid md:grid-cols-2 gap-12 items-center relative">
      <div data-aos="fade-right">
        <h1
          class="text-5xl md:text-7xl font-extrabold mb-6 leading-tight"
          :class="isDark ? 'text-white' : 'text-black'"
        >
          Hello, I'm <span class="gradient-text">MAHEDI HASAN</span>
        </h1>
        <div class="text-2xl md:text-3xl font-medium text-gray-300 mb-8 h-12">
          <span ref="typeTarget"></span>
        </div>
        <p class="text-gray-400 text-lg mb-10 max-w-xl leading-relaxed">
          Full Stack Web Developer specialized in building exceptional digital experiences. 
          I turn complex problems into elegant, user-friendly solutions.
        </p>
        <div class="flex flex-wrap gap-4">
          <a href="#contact" class="px-8 py-4 bg-blue-600 hover:bg-blue-700 text-white font-semibold rounded-full transition-all transform hover:-translate-y-1 shadow-lg shadow-blue-600/20">
            Hire Me
          </a>
          <a
            href="/src/assets/CV of Mahedi Hasan (Software Developer).pdf"
            target="_blank"
            class="px-8 py-4 border border-blue-600/40 hover:border-blue-500 font-semibold rounded-full transition-all hover:bg-blue-500/10"
            :class="isDark ? 'text-white' : 'text-black'"
          >
            Download CV
          </a>
        </div>
        
        <div class="mt-12 flex space-x-4">
          <a
            v-for="social in socials"
            :key="social.name"
            :href="social.link"
            target="_blank"
            class="w-11 h-11 rounded-full border border-gray-700 hover:border-blue-500/70 flex items-center justify-center text-gray-300 hover:text-white transition-all"
          >
            <component :is="social.icon" class="w-5 h-5" />
          </a>
        </div>
      </div>
      
      <div class="relative flex flex-col items-center gap-4" data-aos="fade-left">
        <h4 class="text-white font-medium tracking-widest uppercase text-center">
          Welcome to my portfolio
        </h4>
        <div class="w-72 h-72 md:w-[450px] md:h-[450px] relative">
          <div class="absolute -top-6 -left-8 w-56 h-56 bg-blue-600/20 rounded-full blur-3xl"></div>
          <div class="absolute -bottom-6 -right-8 w-64 h-64 bg-purple-600/20 rounded-full blur-3xl"></div>
          
          <div class="relative w-full h-full rounded-2xl overflow-hidden border border-blue-500/30 bg-gray-900 shadow-2xl p-1 bg-gradient-to-b from-blue-500/20 via-transparent to-purple-500/20">
            <img 
              src="/src/assets/images/Mahedi.png" 
              alt="Mahedi Hasan" 
              class="w-full h-full object-cover object-top -translate-y-5 md:-translate-y-10 transition-all duration-700 rounded-xl"
            />
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { onMounted, ref } from 'vue'
import Typed from 'typed.js'
import { Linkedin, Github, Facebook, Instagram } from 'lucide-vue-next'

const props = defineProps({
  isDark: Boolean
})

const typeTarget = ref(null)

const socials = [
  { name: 'LinkedIn', link: 'https://www.linkedin.com/in/mahedihasan8/', icon: Linkedin },
  { name: 'GitHub', link: 'https://github.com/ProgrammerMahediHasan', icon: Github },
  { name: 'Facebook', link: 'https://www.facebook.com/MahediHasanAbir8/', icon: Facebook },
  { name: 'Instagram', link: 'https://www.instagram.com/mahedi_hasan_abir8/', icon: Instagram }
]

onMounted(() => {
  new Typed(typeTarget.value, {
    strings: [
      'Full Stack Web Developer',
      'Laravel Specialist',
      'Vue.js Enthusiast',
      'MySQL & Oracle Database Specialist',
      'UI/UX Designer'
    ],
    typeSpeed: 50,
    backSpeed: 30,
    loop: true,
    backDelay: 2000
  })
})
</script>

<style scoped>
.min-height-screen {
  min-height: calc(100vh - 80px);
}
</style>
