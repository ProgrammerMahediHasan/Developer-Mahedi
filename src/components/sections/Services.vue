<template>
  <section id="services" class="py-24" :class="isDark ? 'bg-[#0f172a]' : 'bg-white'">
    <div class="container mx-auto px-6">
      <div class="text-center mb-16" data-aos="fade-up">
        <h2 class="text-4xl font-bold mb-4" :class="isDark ? 'text-white' : 'text-slate-900'">My Services</h2>
        <div class="w-20 h-1 bg-blue-600 mx-auto rounded-full"></div>
      </div>

      <div class="grid md:grid-cols-2 lg:grid-cols-4 gap-8">
        <div 
          v-for="(service, index) in services" 
          :key="index" 
          class="group p-8 rounded-2xl transition-all duration-500 transform hover:-translate-y-2 shadow-xl"
          :class="isDark ? 'bg-[#1e293b]/30 border border-gray-800 hover:border-blue-500/50 hover:bg-[#1e293b]/50' : 'bg-white border border-slate-200 hover:border-blue-500/40 hover:bg-blue-50/30'"
          data-aos="fade-up" 
          :data-aos-delay="index * 100"
        >
          <div class="w-16 h-16 rounded-xl flex items-center justify-center mb-6 transition-all duration-500" :class="isDark ? 'bg-blue-600/10 group-hover:bg-blue-600' : 'bg-blue-600/10 group-hover:bg-blue-600'">
            <component :is="service.icon" class="w-8 h-8 text-blue-500 transition-all duration-500" :class="isDark ? 'group-hover:text-white' : 'group-hover:text-white'" />
          </div>
          <h3 class="text-xl font-bold mb-4" :class="isDark ? 'text-white' : 'text-slate-900'">{{ service.title }}</h3>
          <p class="leading-relaxed mb-6" :class="isDark ? 'text-gray-400' : 'text-slate-600'">
            {{ service.description }}
          </p>
          <a href="#" class="text-blue-600 font-medium flex items-center group-hover:translate-x-2 transition-transform">
            Learn More <ArrowRight class="w-4 h-4 ml-2" />
          </a>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { Code2, Palette, Database, Search, ArrowRight, Globe, Smartphone, ShieldCheck, Server, Github, Headset } from 'lucide-vue-next'
const props = defineProps({ isDark: Boolean })

const services = [
  {
    title: 'Web Development',
    description: 'Custom websites built with the latest technologies. Fast, secure, and SEO-friendly.',
    icon: Code2
  },
  {
    title: 'UI/UX Design',
    description: 'Modern and intuitive designs focused on user experience and brand identity.',
    icon: Palette
  },
  {
    title: 'API Development',
    description: 'Developing secure RESTful APIs with seamless third-party integration and scalable logic.',
    icon: Server
  },
  {
    title: 'Git/GitHub',
    description: 'Expert version control, branch management, and seamless code collaboration.',
    icon: Github
  },
  {
    title: 'E-commerce',
    description: 'Full-featured online stores with secure payment integration and management.',
    icon: Globe
  },
  {
    title: 'App Design',
    description: 'Designing intuitive, user-centric mobile and web app interfaces for a premium experience.',
    icon: Smartphone
  },
  {
    title: 'Database Maintenance',
    description: 'Ensure data integrity, optimize performance, and secure backups daily.',
    icon: Database
  },
  {
    title: 'Client Support',
    description: 'Ongoing support 24/7 technical assistance, troubleshooting, and reliable client support.',
    icon: Headset
  }
]
</script>
