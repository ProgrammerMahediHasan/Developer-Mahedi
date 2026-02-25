<template>
  <section id="portfolio" class="py-24" :class="isDark ? 'bg-[#0f172a]' : 'bg-[#f9fafb]'">
    <div class="container mx-auto px-6">
      <div class="text-center mb-16" data-aos="fade-up">
        <h2 class="text-4xl font-bold mb-4" :class="isDark ? 'text-white' : 'text-slate-900'">My Projects</h2>
        <div class="w-20 h-1 bg-blue-600 mx-auto rounded-full"></div>
      </div>

      <!-- Filter Tabs -->
      <div class="flex flex-wrap justify-center gap-4 mb-12" data-aos="fade-up">
        <button 
          v-for="tab in tabs" 
          :key="tab"
          @click="activeTab = tab"
          :class="[
            'px-6 py-2 rounded-full font-medium transition-all duration-300 border',
            activeTab === tab 
              ? 'bg-blue-600 text-white shadow-lg shadow-blue-600/20 border-blue-600' 
              : (isDark ? 'text-gray-300 hover:text-white border-gray-700 hover:border-blue-500/50' : 'text-slate-700 hover:text-slate-900 border-slate-200 hover:border-blue-500/50 bg-white')
          ]"
        >
          {{ tab }}
        </button>
      </div>

      <!-- Projects Grid -->
      <div class="grid md:grid-cols-2 lg:grid-cols-3 gap-8">
        <div 
          v-for="(project, index) in filteredProjects" 
          :key="index"
          class="group relative overflow-hidden rounded-2xl transition-all duration-500 shadow-xl hover:-translate-y-1"
          :class="isDark ? 'bg-[#0f172a] border border-gray-800 hover:border-blue-500/50' : 'bg-white border border-slate-200 hover:border-blue-500/40'"
          data-aos="fade-up"
          :data-aos-delay="index * 100"
        >
          <!-- Project Image -->
          <div class="aspect-video overflow-hidden">
            <img 
              :src="project.image" 
              :alt="project.title" 
              class="w-full h-full object-cover group-hover:scale-110 transition-transform duration-700"
            />
          </div>

          <!-- Overlay -->
          <div class="absolute inset-0 bg-gradient-to-t opacity-0 group-hover:opacity-100 transition-opacity duration-500 flex flex-col justify-end p-8" :class="isDark ? 'from-[#0f172a] via-[#0f172a]/80 to-transparent' : 'from-white via-white/90 to-transparent'">
            <span class="text-blue-500 text-sm font-medium mb-2 uppercase tracking-widest">{{ project.category }}</span>
            <h3 class="text-2xl font-bold mb-3" :class="isDark ? 'text-white' : 'text-slate-900'">{{ project.title }}</h3>
            <p class="text-sm mb-6 line-clamp-2" :class="isDark ? 'text-gray-300' : 'text-slate-600'">{{ project.description }}</p>
            
            <div class="flex space-x-4">
              <a :href="project.liveLink" class="p-3 bg-blue-600 rounded-full text-white hover:bg-blue-700 transition-colors shadow-lg" target="_blank">
                <ExternalLink class="w-5 h-5" />
              </a>
              <a :href="project.githubLink" class="p-3 rounded-full text-white transition-colors shadow-lg" :class="isDark ? 'bg-gray-800 hover:bg-gray-700' : 'bg-slate-800 hover:bg-slate-700'" target="_blank">
                <Github class="w-5 h-5" />
              </a>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, computed } from 'vue'
import { ExternalLink, Github } from 'lucide-vue-next'
import FoodCourtBackend from '../../assets/images/FoodCourt_Backend.png'
import NextPrimeHRMS from '../../assets/images/NextPrimeHRMS.png'
import AbirsFoodCourtPOS from '../../assets/images/Abirs_FoodCourt_POS.png'
import SoftCodeHRMS from '../../assets/images/SoftCodeHRMS.png'
import SohozLandingPage from '../../assets/images/Sohoz-Landing-Page.png'
import SofTechLandingPage from '../../assets/images/SofTech-Landing-Page.png'
import InnoCraftLandingPage from '../../assets/images/InnoCraft-Landing-Page.png'
const props = defineProps({ isDark: Boolean })

const tabs = ['All', 'Frontend-Project', 'Backend-Project', 'Landing Page-Project']
const activeTab = ref('All')

const projects = [
  {
    title: "Restaurant Management System",
    category: 'Backend-Project',
    image: FoodCourtBackend,
    description: 'Laravel-based restaurant management: roles, menus, orders, billing, and delivery.',
    liveLink: 'http://mahedi.intelsofts.com/Abirs_FoodCourt/public/login',
    githubLink: '#'
  },
  {
    title: "Human Resource Management System",
    category: 'Backend-Project',
    image: NextPrimeHRMS,
    description: 'Laravel-based human resource management system with employee tracking and payroll features.',
    liveLink: 'http://mahedi.intelsofts.com/NextPrime_Limited/admin/',
    githubLink: '#'
  },

  {
    title: 'Restaurant Managment System POS',
    category: 'Frontend-Project',
    image: AbirsFoodCourtPOS,
    description: 'A comprehensive admin dashboard built with Laravel and Vue 3.',
    liveLink: 'http://mahedi.intelsofts.com/Abirs_FoodCourt_Frontend/login',
    githubLink: '#'
  },

  {
    title: 'Human Resource Management System-Frontend',
    category: 'Frontend-Project',
    image: SoftCodeHRMS,
    description: 'A comprehensive HRMS admin dashboard built with React for the frontend and Laravel for the backend, designed to manage employees, payroll, attendance, and HR operations efficiently.',
    liveLink: 'http://mahedi.intelsofts.com/SoftCode/',
    githubLink: '#'
  },

  // {
  //   title: 'Modern Portfolio Template',
  //   category: 'UI Design',
  //   image: 'https://picsum.photos/seed/project2/800/600',
  //   description: 'A sleek, minimalist portfolio design for creative professionals.',
  //   liveLink: '#',
  //   githubLink: '#'
  // },
  // {
  //   title: 'Real-time Chat App',
  //   category: 'Web Apps',
  //   image: 'https://picsum.photos/seed/project3/800/600',
  //   description: 'Real-time messaging application using Node.js and Socket.io.',
  //   liveLink: '#',
  //   githubLink: '#'
  // },
  // {
  //   title: 'Fintech Mobile UI',
  //   category: 'UI Design',
  //   image: 'https://picsum.photos/seed/project4/800/600',
  //   description: 'Mobile banking app interface with dark mode support.',
  //   liveLink: '#',
  //   githubLink: '#'
  // },

  {
    title: 'Sohoz-Landing-Page',
    category: 'Landing Page-Project',
    image: SohozLandingPage,
    description: 'A responsive clone of the Sohoz landing page, built with modern frontend technologies, focusing on clean UI design, smooth layout structure, and pixel-perfect responsiveness across all devices.',
    liveLink: 'http://mahedi.intelsofts.com/Shohoz-Project/Air.html',
    githubLink: '#'
  },

  {
    title: 'SofTech-Landing-Page',
    category: 'Landing Page-Project',
    image: SofTechLandingPage,
    description: 'Softech Demo Website is a full-stack web project showcasing responsive frontend design, backend integration, and dynamic data handling.',
    liveLink: 'http://mahedi.intelsofts.com/SofTech/',
    githubLink: '#'
  },

  {
    title: 'InnoCraft-Landing-Page',
    category: 'Landing Page-Project',
    image: InnoCraftLandingPage,
    description: 'InnoCraft Demo Website is a full-stack web project showcasing responsive frontend design, backend integration, and dynamic data handling.',
    liveLink: 'https://programmermahedihasan.github.io/InnoCraft/',
    githubLink: '#'
  }

]

const filteredProjects = computed(() => {
  if (activeTab.value === 'All') return projects
  return projects.filter(project => project.category === activeTab.value)
})
</script>
