<template>
  <section id="contact" class="py-24" :class="isDark ? 'bg-[#0f172a]' : 'bg-white'">
    <div class="container mx-auto px-6">
      <div class="text-center mb-16" data-aos="fade-up">
        <h2 class="text-4xl font-bold mb-4" :class="isDark ? 'text-white' : 'text-slate-900'">Get In Touch</h2>
        <div class="w-20 h-1 bg-blue-600 mx-auto rounded-full"></div>
      </div>

      <div class="grid lg:grid-cols-3 gap-12">
        <!-- Contact Info -->
        <div class="space-y-8" data-aos="fade-right">
          <div v-for="(info, index) in contactInfo" :key="index" class="flex items-start group">
            <div class="w-12 h-12 rounded-xl flex items-center justify-center mr-4 group-hover:bg-blue-600 transition-colors duration-300" :class="isDark ? 'bg-[#1e293b]' : 'bg-slate-100'">
              <component :is="info.icon" class="w-6 h-6 text-blue-500 group-hover:text-white transition-colors" />
            </div>
            <div>
              <h4 class="font-bold mb-1" :class="isDark ? 'text-white' : 'text-slate-900'">{{ info.label }}</h4>
              <p class="text-sm leading-relaxed" :class="isDark ? 'text-gray-400' : 'text-slate-600'">{{ info.value }}</p>
            </div>
          </div>

          <!-- Map Embed -->
          <div class="rounded-2xl overflow-hidden h-64 mt-12 transition-all duration-500" :class="isDark ? 'border border-gray-800' : 'border border-slate-200'">
            <iframe 
              src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d233668.3870369269!2d90.27923991057244!3d23.780573258035957!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x3755b8b087026b81%3A0x8fa5690c31864291!2sDhaka!5e0!3m2!1sen!2sbd!4v1625478335431!5m2!1sen!2sbd" 
              width="100%" 
              height="100%" 
              style="border:0;" 
              allowfullscreen="" 
              loading="lazy"
            ></iframe>
          </div>
        </div>

        <!-- Contact Form -->
        <div class="lg:col-span-2" data-aos="fade-left">
          <div class="rounded-2xl p-8 md:p-10 transition-all shadow-xl" :class="isDark ? 'bg-[#0f172a] border border-gray-800' : 'bg-white border border-slate-200'">
            <div class="mb-8">
              <h3 class="text-2xl font-bold mb-2" :class="isDark ? 'text-white' : 'text-slate-900'">Send me a message</h3>
              <p class="text-sm" :class="isDark ? 'text-gray-400' : 'text-slate-600'">I usually reply within 24 hours</p>
              <div class="flex flex-wrap gap-2 mt-4">
                <span class="px-3 py-1 text-xs rounded-full border text-blue-600 bg-blue-600/10 border-blue-600/30">Available for freelance</span>
                <span class="px-3 py-1 text-xs rounded-full border text-emerald-600 bg-emerald-600/10 border-emerald-600/30">Quick response</span>
              </div>
            </div>
          <form @submit.prevent="handleSubmit" class="space-y-6">
            <div class="grid md:grid-cols-2 gap-6">
              <div class="space-y-2">
                <label class="text-gray-400 text-sm font-medium ml-1">Your Name</label>
                <div class="relative">
                  <User class="w-5 h-5 absolute left-4 top-1/2 -translate-y-1/2" :class="isDark ? 'text-gray-400' : 'text-slate-500'"/>
                  <input 
                    v-model="form.name"
                    type="text" 
                    placeholder="John Doe"
                    required
                    name="name"
                    class="w-full rounded-xl pl-12 px-6 py-4 focus:outline-none focus:ring-2 focus:ring-blue-500/40 transition-colors" :class="isDark ? 'bg-[#1e293b]/60 border border-gray-800 text-white' : 'bg-white border border-slate-200 text-slate-900'"
                  >
                </div>
              </div>
              <div class="space-y-2">
                <label class="text-gray-400 text-sm font-medium ml-1">Email Address</label>
                <div class="relative">
                  <AtSign class="w-5 h-5 absolute left-4 top-1/2 -translate-y-1/2" :class="isDark ? 'text-gray-400' : 'text-slate-500'"/>
                  <input 
                    v-model="form.email"
                    type="email" 
                    placeholder="john@example.com"
                    required
                    name="email"
                    class="w-full rounded-xl pl-12 px-6 py-4 focus:outline-none focus:ring-2 focus:ring-blue-500/40 transition-colors" :class="isDark ? 'bg-[#1e293b]/60 border border-gray-800 text-white' : 'bg-white border border-slate-200 text-slate-900'"
                  >
                </div>
              </div>
            </div>

            <div class="space-y-2">
              <label class="text-gray-400 text-sm font-medium ml-1">Subject</label>
              <div class="relative">
                <FileText class="w-5 h-5 absolute left-4 top-1/2 -translate-y-1/2" :class="isDark ? 'text-gray-400' : 'text-slate-500'"/>
                <input 
                  v-model="form.subject"
                  type="text" 
                  placeholder="Project Inquiry"
                  required
                  name="subject"
                  class="w-full rounded-xl pl-12 px-6 py-4 focus:outline-none focus:ring-2 focus:ring-blue-500/40 transition-colors" :class="isDark ? 'bg-[#1e293b]/60 border border-gray-800 text-white' : 'bg-white border border-slate-200 text-slate-900'"
                >
              </div>
            </div>

            <div class="space-y-2">
              <label class="text-gray-400 text-sm font-medium ml-1">Message</label>
              <div class="relative">
                <MessageSquare class="w-5 h-5 absolute left-4 top-4" :class="isDark ? 'text-gray-400' : 'text-slate-500'"/>
                <textarea 
                  v-model="form.message"
                  rows="6" 
                  placeholder="Tell me about your project..."
                  required
                  name="message"
                  class="w-full rounded-xl pl-12 px-6 py-4 focus:outline-none focus:ring-2 focus:ring-blue-500/40 transition-colors resize-none" :class="isDark ? 'bg-[#1e293b]/60 border border-gray-800 text-white' : 'bg-white border border-slate-200 text-slate-900'"
                ></textarea>
              </div>
            </div>

            <button 
              type="submit" 
              :disabled="isSubmitting"
              class="w-full md:w-auto px-12 py-4 bg-blue-600 hover:bg-blue-700 text-white font-bold rounded-full transition-all shadow-lg shadow-blue-600/20 disabled:opacity-50 flex items-center justify-center"
            >
              <Send v-if="!isSubmitting" class="w-5 h-5 mr-2" />
              <Loader2 v-else class="w-5 h-5 mr-2 animate-spin" />
              {{ isSubmitting ? 'Sending...' : 'Send Message' }}
            </button>
            
            <p v-if="submitStatus" :class="[
              'text-sm font-medium transition-opacity duration-300',
              submitStatus.type === 'success' ? 'text-green-500' : 'text-red-500'
            ]">
              {{ submitStatus.message }}
            </p>
          </form>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, reactive, onMounted } from 'vue'
import emailjs from '@emailjs/browser'
import { Mail, Phone, MapPin, Send, Loader2, User, AtSign, FileText, MessageSquare } from 'lucide-vue-next'
const props = defineProps({ isDark: Boolean })

const form = reactive({
  name: '',
  email: '',
  subject: '',
  message: ''
})

const isSubmitting = ref(false)
const submitStatus = ref(null)
const nextUrl = ref('')

const contactInfo = [
  { icon: Mail, label: 'Email Me', value: 'mahedihasanabir8@gmail.com' },
  { icon: Phone, label: 'Call Me', value: '01632606827' },
  { icon: MapPin, label: 'Location', value: 'Narayanganj, Dhaka' }
]

onMounted(() => {
  nextUrl.value = `${window.location.origin}/#contact?sent=1`
  const hash = window.location.hash || ''
  const hasSent = hash.includes('sent=1')
  if (hasSent) {
    submitStatus.value = {
      type: 'success',
      message: 'Thank you! Your message has been sent. If this is your first time, please check your inbox for a verification email.'
    }
    // Optional: clean hash (not strictly necessary)
  }
})

const handleSubmit = async () => {
  isSubmitting.value = true
  submitStatus.value = null
  try {
    const serviceId = import.meta.env.VITE_EMAILJS_SERVICE_ID
    const templateId = import.meta.env.VITE_EMAILJS_TEMPLATE_ID
    const publicKey = import.meta.env.VITE_EMAILJS_PUBLIC_KEY

    if (serviceId && templateId && publicKey) {
      emailjs.init(publicKey)
      await emailjs.send(serviceId, templateId, {
        from_name: form.name,
        reply_to: form.email,
        subject: form.subject,
        message: form.message,
        to_email: 'mahedihasanabir8@gmail.com'
      })
      submitStatus.value = {
        type: 'success',
        message: 'Thank you! Your message has been sent.'
      }
      form.name = ''
      form.email = ''
      form.subject = ''
      form.message = ''
    } else {
      const formEl = document.createElement('form')
      formEl.action = 'https://formsubmit.co/mahedihasanabir8@gmail.com'
      formEl.method = 'POST'
      formEl.style.display = 'none'
      const fields = {
        name: form.name,
        email: form.email,
        subject: form.subject || 'New inquiry',
        message: form.message,
        _template: 'table',
        _next: nextUrl.value,
        _replyto: form.email,
        _subject: `New inquiry • Portfolio — ${form.subject || 'No subject'} by ${form.name}`,
        page: window.location.href,
        time: new Date().toLocaleString(),
        _autoresponse: `Hi ${form.name},\n\nThanks for reaching out! I received your message and will reply shortly.\n\n— Mahedi`
      }
      Object.entries(fields).forEach(([k, v]) => {
        const input = document.createElement('input')
        input.type = 'hidden'
        input.name = k
        input.value = v
        formEl.appendChild(input)
      })
      document.body.appendChild(formEl)
      formEl.submit()
    }
  } catch (e) {
    submitStatus.value = {
      type: 'error',
      message: 'Something went wrong. Please try again later.'
    }
  } finally {
    isSubmitting.value = false
  }
}
</script>
