<script setup>
import { ref, onMounted, watch } from 'vue'
import {
  CodeBracketIcon,
  ServerIcon,
  CircleStackIcon,
  ArrowDownTrayIcon
} from '@heroicons/vue/24/outline'

const darkMode = ref(false)

// Handle dark mode toggle on HTML element
onMounted(() => {
  if (window.matchMedia && window.matchMedia('(prefers-color-scheme: dark)').matches) {
    darkMode.value = true;
  }
  updateDarkMode()
})

watch(darkMode, () => {
  updateDarkMode()
})

function updateDarkMode() {
  if (darkMode.value) {
    document.documentElement.classList.add('dark')
  } else {
    document.documentElement.classList.remove('dark')
  }
}

const projects = [
  {
    title: 'IT Asset Monitoring System (QCC Initiative)',
    tech: 'Laravel, API Integration, QR Code Scanner',
    desc: 'Sistem pelacakan dan verifikasi hardware antar departemen untuk efisiensi audit internal.',
    impact: 'Meningkatkan akurasi dan kecepatan audit aset.',
    image: 'https://picsum.photos/seed/asset/600/400'
  },
  {
    title: 'Industrial Production Forecast & Monitoring',
    tech: 'Web-based Dashboard, Database Optimization',
    desc: 'Sistem pemantauan kapasitas produksi industri harian dan kalkulasi persentase forecast data.',
    impact: 'Memudahkan pengambilan keputusan harian berbasis data waktu nyata.',
    image: 'https://picsum.photos/seed/industry/600/400'
  },
  {
    title: 'Enterprise Approval Workflow Engine',
    tech: 'PHP/Python Backend, Multi-stage Verification',
    desc: 'Automasi alur persetujuan dokumen digital yang melibatkan multi-user dan digital signatures.',
    impact: 'Memangkas waktu proses approval birokrasi lebih dari 50%.',
    image: 'https://picsum.photos/seed/workflow/600/400'
  },
  {
    title: 'Smart Farming IoT Dashboard',
    tech: 'IoT Sensor Integration, Laravel Dashboard',
    desc: 'Mengubah data mentah sensor pertanian menjadi grafik visual insight yang mudah dipahami.',
    impact: 'Membantu optimalisasi hasil panen dan efisiensi air.',
    image: 'https://picsum.photos/seed/farming/600/400'
  }
]
</script>

<template>
  <div class="min-h-screen bg-gray-50 dark:bg-gray-900 text-gray-900 dark:text-gray-100 font-sans transition-colors duration-300">
    
    <!-- Navbar / Header -->
    <nav class="sticky top-0 z-50 backdrop-blur-md bg-white/70 dark:bg-gray-900/70 border-b border-gray-200 dark:border-gray-800 transition-colors">
      <div class="max-w-4xl mx-auto px-4 py-4 flex justify-between items-center">
        <div class="font-bold text-xl tracking-tight">Tobias.dev</div>
        <button @click="darkMode = !darkMode" class="p-2 rounded-full hover:bg-gray-200 dark:hover:bg-gray-800 transition-colors" aria-label="Toggle Dark Mode">
          <span v-if="darkMode" class="text-yellow-400">☀️</span>
          <span v-else class="text-gray-600">🌙</span>
        </button>
      </div>
    </nav>

    <main class="max-w-4xl mx-auto px-4 py-12">
      
      <!-- Section 1: Hero & Quick Bio -->
      <section class="py-12 md:py-20 flex flex-col-reverse md:flex-row gap-12 items-center border-b border-gray-200 dark:border-gray-800">
        <div class="flex-1 space-y-6 text-center md:text-left">
          <h1 class="text-4xl md:text-6xl font-extrabold tracking-tight">
            Hi, I'm <span class="text-indigo-600 dark:text-indigo-400">Tobias Mikha S.</span>
          </h1>
          <h2 class="text-xl md:text-2xl font-medium text-gray-600 dark:text-gray-300">
            Full-Stack Web & Mobile Developer
          </h2>
          <p class="text-lg text-gray-600 dark:text-gray-400 max-w-2xl leading-relaxed mx-auto md:mx-0">
            Jago ngoding backend (Laravel/Python) sekaligus frontend (Vue/React), berpengalaman megang database enterprise (MySQL, SQL Server, DB2), dan terbiasa dengan standardisasi industri (QCC & Digital Workflow Automation).
          </p>
          <div class="flex flex-wrap justify-center md:justify-start gap-4 pt-4">
            <a href="#" class="inline-flex items-center gap-2 bg-indigo-600 hover:bg-indigo-700 text-white px-6 py-3 rounded-lg font-medium transition-colors shadow-lg shadow-indigo-200 dark:shadow-none">
              <ArrowDownTrayIcon class="w-5 h-5" /> Download CV
            </a>
            <a href="https://github.com/tobiasms" target="_blank" class="inline-flex items-center gap-2 bg-white dark:bg-gray-800 border border-gray-200 dark:border-gray-700 hover:bg-gray-50 dark:hover:bg-gray-700 px-6 py-3 rounded-lg font-medium transition-colors shadow-sm">
              GitHub
            </a>
            <a href="https://linkedin.com/in/tobias-mikha-s" target="_blank" class="inline-flex items-center gap-2 bg-white dark:bg-gray-800 border border-gray-200 dark:border-gray-700 hover:bg-gray-50 dark:hover:bg-gray-700 px-6 py-3 rounded-lg font-medium transition-colors shadow-sm">
              LinkedIn
            </a>
          </div>
        </div>
        <div class="w-48 h-48 md:w-64 md:h-64 shrink-0 rounded-full overflow-hidden border-4 border-indigo-100 dark:border-gray-800 shadow-xl">
          <img src="https://images.unsplash.com/photo-1537511446984-935f663eb1f4?auto=format&fit=crop&w=400&h=400&q=80" alt="Tobias Mikha S." class="w-full h-full object-cover" />
        </div>
      </section>

      <!-- Section 2: Core Skill Badges -->
      <section class="py-16 border-b border-gray-200 dark:border-gray-800">
        <h3 class="text-2xl font-bold mb-8 text-center md:text-left">Core Expertise</h3>
        <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
          
          <div class="p-6 bg-white dark:bg-gray-800 rounded-xl shadow-sm border border-gray-100 dark:border-gray-700 hover:shadow-md transition-shadow">
            <div class="w-12 h-12 bg-blue-100 dark:bg-blue-900/40 text-blue-600 dark:text-blue-400 rounded-lg flex items-center justify-center mb-4">
              <ServerIcon class="w-6 h-6" />
            </div>
            <h4 class="text-lg font-semibold mb-2">Backend</h4>
            <p class="text-gray-600 dark:text-gray-400">PHP (Laravel), Python (Django, FastAPI)</p>
          </div>

          <div class="p-6 bg-white dark:bg-gray-800 rounded-xl shadow-sm border border-gray-100 dark:border-gray-700 hover:shadow-md transition-shadow">
            <div class="w-12 h-12 bg-emerald-100 dark:bg-emerald-900/40 text-emerald-600 dark:text-emerald-400 rounded-lg flex items-center justify-center mb-4">
              <CodeBracketIcon class="w-6 h-6" />
            </div>
            <h4 class="text-lg font-semibold mb-2">Frontend/Mobile</h4>
            <p class="text-gray-600 dark:text-gray-400">Vue.js, React, Ionic Framework</p>
          </div>

          <div class="p-6 bg-white dark:bg-gray-800 rounded-xl shadow-sm border border-gray-100 dark:border-gray-700 hover:shadow-md transition-shadow">
            <div class="w-12 h-12 bg-purple-100 dark:bg-purple-900/40 text-purple-600 dark:text-purple-400 rounded-lg flex items-center justify-center mb-4">
              <CircleStackIcon class="w-6 h-6" />
            </div>
            <h4 class="text-lg font-semibold mb-2">Databases & DevOps</h4>
            <p class="text-gray-600 dark:text-gray-400">MySQL, SQL Server, IBM DB2, Nginx, Linux</p>
          </div>

        </div>
      </section>

      <!-- Section 3: Highlighted Projects -->
      <section class="py-16 border-b border-gray-200 dark:border-gray-800">
        <h3 class="text-2xl font-bold mb-8 text-center md:text-left">Highlighted Projects</h3>
        <div class="space-y-12">
          <div v-for="(project, index) in projects" :key="index" class="group relative flex flex-col md:flex-row gap-8 items-center bg-white dark:bg-gray-800 rounded-2xl p-6 shadow-sm border border-gray-100 dark:border-gray-700 hover:shadow-md transition-shadow">
            
            <div class="w-full md:w-1/3 aspect-video rounded-xl overflow-hidden shrink-0 bg-gray-100 dark:bg-gray-900 relative">
              <img :src="project.image" :alt="project.title" class="w-full h-full object-cover group-hover:scale-105 transition-transform duration-500" />
            </div>
            
            <div class="flex-1">
              <h4 class="text-xl font-bold mb-2 group-hover:text-indigo-600 dark:group-hover:text-indigo-400 transition-colors">
                {{ project.title }}
              </h4>
              <div class="text-sm font-mono text-indigo-600 dark:text-indigo-400 mb-4 bg-indigo-50 dark:bg-indigo-900/20 inline-block px-2 py-1 rounded">
                {{ project.tech }}
              </div>
              <p class="text-gray-700 dark:text-gray-300 mb-4 leading-relaxed">
                {{ project.desc }}
              </p>
              <div class="inline-flex items-center text-sm text-gray-600 dark:text-gray-400 bg-gray-50 dark:bg-gray-900 px-3 py-2 rounded-lg border border-gray-200 dark:border-gray-700 w-full md:w-auto">
                <span class="font-semibold mr-2 text-gray-900 dark:text-gray-100">Impact:</span> {{ project.impact }}
              </div>
            </div>

          </div>
        </div>
      </section>

      <!-- Section 4: Contact / Footer -->
      <section class="py-16 text-center">
        <h3 class="text-3xl font-bold mb-4">Let's work together</h3>
        <p class="text-gray-600 dark:text-gray-400 mb-8 max-w-lg mx-auto text-lg">
          Tertarik untuk berdiskusi lebih lanjut tentang bagaimana saya bisa berkontribusi pada tim Anda? Mari terhubung.
        </p>
        <div class="flex flex-col sm:flex-row justify-center gap-4">
          <a href="mailto:contact@example.com" class="bg-indigo-600 hover:bg-indigo-700 text-white px-8 py-3.5 rounded-lg font-medium transition-all shadow-lg shadow-indigo-200 dark:shadow-none hover:-translate-y-0.5">
            Email Me
          </a>
          <a href="https://wa.me/6281234567890" target="_blank" class="bg-emerald-600 hover:bg-emerald-700 text-white px-8 py-3.5 rounded-lg font-medium transition-all shadow-lg shadow-emerald-200 dark:shadow-none hover:-translate-y-0.5">
            WhatsApp
          </a>
        </div>
      </section>

    </main>

    <footer class="py-8 text-center text-gray-500 dark:text-gray-500 text-sm border-t border-gray-200 dark:border-gray-800 mt-auto">
      &copy; 2026 Tobias Mikha Sulistiyo. All rights reserved.
    </footer>
  </div>
</template>

<style>
/* Any non-tailwind specific overrides */
</style>
