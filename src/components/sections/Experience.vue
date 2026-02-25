<template>
  <section id="experience" class="py-24" :class="isDark ? 'bg-[#0f172a]' : 'bg-[#f9fafb]'">
    <div class="container mx-auto px-6">
      <div class="text-center mb-16" data-aos="fade-up">
        <h2 class="text-4xl font-bold mb-4" :class="isDark ? 'text-white' : 'text-slate-900'">Experience & Education</h2>
        <div class="w-20 h-1 bg-blue-600 mx-auto rounded-full"></div>
      </div>

      <div class="max-w-4xl mx-auto">
        <div class="relative">
          <!-- Vertical Line -->
          <div class="absolute left-0 md:left-1/2 transform md:-translate-x-1/2 w-0.5 h-full" :class="isDark ? 'bg-gray-800' : 'bg-slate-200'"></div>

          <!-- Timeline Items -->
          <div v-for="(item, index) in timeline" :key="index" class="mb-12 relative flex flex-col md:flex-row items-center">
            <!-- Dot -->
            <div class="absolute left-0 md:left-1/2 transform -translate-x-1/2 w-4 h-4 rounded-full bg-blue-600 border-4 z-10" :class="isDark ? 'border-[#0f172a]' : 'border-[#f9fafb]'"></div>

            <!-- Content -->
            <div 
              :class="[
                'w-full md:w-1/2 pl-8 md:pl-0',
                index % 2 === 0 ? 'md:pr-12 md:text-right' : 'md:ml-auto md:pl-12'
              ]"
              data-aos="fade-up"
              :data-aos-delay="index * 100"
            >
              <div class="p-6 rounded-2xl transition-all duration-300" :class="isDark ? 'bg-[#1e293b]/50 border border-gray-800 hover:border-blue-500/30' : 'bg-white border border-slate-200 hover:border-blue-500/40'">
                <span class="text-blue-600 font-bold text-sm uppercase tracking-widest mb-2 block">{{ item.date }}</span>
                <h3 class="text-xl font-bold mb-1" :class="isDark ? 'text-white' : 'text-slate-900'">{{ item.title }}</h3>
                <h4 class="font-medium mb-4" :class="isDark ? 'text-gray-400' : 'text-slate-600'">{{ item.company }}</h4>
                <p class="text-sm leading-relaxed" :class="isDark ? 'text-gray-500' : 'text-slate-600'">{{ item.description }}</p>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
const props = defineProps({ isDark: Boolean })
const timeline = [
  {
    date: '2025 - Present',
    title: 'Junior Software Developer',
    company: 'Intellect Software Ltd. ',
    description: 'Lead developer for major e-commerce platforms. Improved site performance by 40% and mentored junior developers.'
  },
  {
    date: '2020 - 2025',
    title: 'Junior Software Programmer',
    company: 'Square InformatiX Ltd.',
    description: 'Experience Worked with Square Toiletries and Square Food & Beverage Ltd on Distribution Management System (DMS).'
  },
  
  {
    date: '2022 - 2023',
    title: 'master of business administration',
    company: 'government tolaram college',
    description: 'Accounting & Finance focuses on managing financial records, analyzing data, and making strategic decisions to ensure business profitability and sustainability.'
  }
]
</script>
