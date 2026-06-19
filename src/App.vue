<script setup>
import { ref, onMounted, watch } from 'vue'
import {
  CodeBracketIcon,
  ServerIcon,
  CircleStackIcon,
  ArrowDownTrayIcon
} from '@heroicons/vue/24/outline'
import profilePhoto from './assets/photo.jpg'
import cvFile from './assets/CV-TOBIAS-MIKHA-S.pdf'
import myLogo from './assets/mylogo.png'
import proj1_1 from './assets/projects/proj1-1.png'
import proj1_2 from './assets/projects/proj1-2.png'
import proj2_1 from './assets/projects/proj2-1.png'
import proj3_1 from './assets/projects/proj3-1.png'
import proj4_1 from './assets/projects/proj4-1.png'

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
    title: 'Smart IoT Farming Dashboard & Monitoring',
    tech: 'Laravel, IoT Sensor Integration, Machine Learning',
    desc: 'Sistem monitoring kebutuhan lahan pertanian secara real-time dengan mengintegrasikan sensor IoT ke dalam dashboard Laravel. Dilengkapi analisa machine learning untuk rekomendasi kondisi lahan.',
    impact: 'Membantu petani memantau kondisi lahan secara real-time dan meningkatkan akurasi prediksi kebutuhan irigasi berbasis data ML.',
    images: [proj1_1, proj1_2]
  },
  {
    title: 'Drowsy / Non-Drowsy Detection System',
    tech: 'Python, TensorFlow, IoT, Real-time Detection',
    desc: 'Sistem deteksi kantuk secara real-time berbasis computer vision. Apabila kondisi drowsy terdeteksi lebih dari 5 detik, sistem akan otomatis memicu buzzer. Dirancang untuk diintegrasikan dengan perangkat IoT saat berkendara.',
    impact: 'Meningkatkan keselamatan berkendara dengan respons otomatis di bawah 1 detik saat terdeteksi tanda-tanda kantuk.',
    images: [proj2_1]
  },
  {
    title: 'ERP Warehouse Order System',
    tech: 'Ionic Framework, JavaScript, Mobile App',
    desc: 'Aplikasi mobile berbasis Ionic yang mencakup alur sistem ERP secara menyeluruh — mulai dari pembelian stok, pencatatan penjualan, hingga pengiriman antar gudang.',
    impact: 'Mengintegrasikan seluruh siklus rantai pasok dalam satu platform mobile, meminimalisasi kesalahan pencatatan stok manual.',
    images: [proj3_1]
  },
  {
    title: 'Website Gereja GKJ Kerten',
    tech: 'Web Development, CMS, Information Portal',
    desc: 'Website resmi gereja yang menggabungkan kebutuhan informasi liturgi dan kegiatan jemaat. Dirancang agar mudah diakses dan dikelola oleh pengurus gereja.',
    impact: 'Mempermudah jemaat mengakses informasi ibadah dan kegiatan gereja kapan saja dan di mana saja.',
    images: [proj4_1],
    link: 'https://gkj-kerten.tob-demo.my.id/'
  }
]

const activeImageIndex = ref({})
function setActiveImage(projectIndex, imgIndex) {
  activeImageIndex.value[projectIndex] = imgIndex
}
function getActiveImage(project, projectIndex) {
  const idx = activeImageIndex.value[projectIndex] ?? 0
  return project.images[idx]
}
</script>

<template>
  <div class="min-h-screen bg-gray-50 dark:bg-gray-900 text-gray-900 dark:text-gray-100 font-sans transition-colors duration-300">
    
    <!-- Navbar / Header -->
    <nav class="sticky top-0 z-50 backdrop-blur-md bg-white/70 dark:bg-gray-900/70 border-b border-gray-200 dark:border-gray-800 transition-colors">
      <div class="max-w-4xl mx-auto px-4 py-4 flex justify-between items-center">
        <img :src="myLogo" alt="Tobias Mikha S." class="h-8 w-auto" />
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
            Seorang Full-Stack Developer berpengalaman yang menguasai pengembangan backend (Laravel, Python) maupun frontend (Vue.js, Ionic), dengan rekam jejak di pengelolaan database enterprise skala industri (MySQL, SQL Server, IBM DB2) serta implementasi sistem digital automation dan IoT. Terbuka untuk kolaborasi project maupun freelance.
          </p>
          <div class="flex flex-wrap justify-center md:justify-start gap-4 pt-4">
            <a :href="cvFile" download class="inline-flex items-center gap-2 bg-indigo-600 hover:bg-indigo-700 text-white px-6 py-3 rounded-lg font-medium transition-colors shadow-lg shadow-indigo-200 dark:shadow-none">
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
          <img :src="profilePhoto" alt="Tobias Mikha S." class="w-full h-full object-cover" />
        </div>
      </section>

      <!-- Section 2: Core Skill Badges -->
      <section class="py-16 border-b border-gray-200 dark:border-gray-800">
        <h3 class="text-2xl font-bold mb-8 text-center md:text-left">Core Expertise</h3>
        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-6">

          <div class="p-6 bg-white dark:bg-gray-800 rounded-xl shadow-sm border border-gray-100 dark:border-gray-700 hover:shadow-md transition-shadow">
            <div class="w-12 h-12 bg-blue-100 dark:bg-blue-900/40 text-blue-600 dark:text-blue-400 rounded-lg flex items-center justify-center mb-4">
              <ServerIcon class="w-6 h-6" />
            </div>
            <h4 class="text-lg font-semibold mb-2">Backend</h4>
            <p class="text-gray-600 dark:text-gray-400 text-sm">PHP (Laravel, CodeIgniter, Native)<br>Python (TensorFlow, Flask, FastAPI, Django)</p>
          </div>

          <div class="p-6 bg-white dark:bg-gray-800 rounded-xl shadow-sm border border-gray-100 dark:border-gray-700 hover:shadow-md transition-shadow">
            <div class="w-12 h-12 bg-emerald-100 dark:bg-emerald-900/40 text-emerald-600 dark:text-emerald-400 rounded-lg flex items-center justify-center mb-4">
              <CodeBracketIcon class="w-6 h-6" />
            </div>
            <h4 class="text-lg font-semibold mb-2">Frontend & Mobile</h4>
            <p class="text-gray-600 dark:text-gray-400 text-sm">JavaScript (Vue.js, Ionic Framework)<br>Crystal Report</p>
          </div>

          <div class="p-6 bg-white dark:bg-gray-800 rounded-xl shadow-sm border border-gray-100 dark:border-gray-700 hover:shadow-md transition-shadow">
            <div class="w-12 h-12 bg-purple-100 dark:bg-purple-900/40 text-purple-600 dark:text-purple-400 rounded-lg flex items-center justify-center mb-4">
              <CircleStackIcon class="w-6 h-6" />
            </div>
            <h4 class="text-lg font-semibold mb-2">Database</h4>
            <p class="text-gray-600 dark:text-gray-400 text-sm">IBM DB2, SQL Server<br>MySQL, SQLite</p>
          </div>

          <div class="p-6 bg-white dark:bg-gray-800 rounded-xl shadow-sm border border-gray-100 dark:border-gray-700 hover:shadow-md transition-shadow">
            <div class="w-12 h-12 bg-orange-100 dark:bg-orange-900/40 text-orange-600 dark:text-orange-400 rounded-lg flex items-center justify-center mb-4">
              <ServerIcon class="w-6 h-6" />
            </div>
            <h4 class="text-lg font-semibold mb-2">DevOps & Infra</h4>
            <p class="text-gray-600 dark:text-gray-400 text-sm">Nginx, Linux<br>IoT Integration</p>
          </div>

        </div>
      </section>

      <!-- Section 3: Highlighted Projects -->
      <section class="py-16 border-b border-gray-200 dark:border-gray-800">
        <h3 class="text-2xl font-bold mb-8 text-center md:text-left">Highlighted Projects</h3>
        <div class="space-y-12">
          <div v-for="(project, index) in projects" :key="index" class="group relative flex flex-col md:flex-row gap-8 items-center bg-white dark:bg-gray-800 rounded-2xl p-6 shadow-sm border border-gray-100 dark:border-gray-700 hover:shadow-md transition-shadow">

            <div class="w-full md:w-1/3 shrink-0">
              <div class="aspect-video rounded-xl overflow-hidden bg-gray-100 dark:bg-gray-900">
                <img :src="getActiveImage(project, index)" :alt="project.title" class="w-full h-full object-cover group-hover:scale-105 transition-transform duration-500" />
              </div>
              <div v-if="project.images.length > 1" class="flex gap-2 mt-2 justify-center">
                <button
                  v-for="(img, imgIdx) in project.images"
                  :key="imgIdx"
                  @click="setActiveImage(index, imgIdx)"
                  class="w-2.5 h-2.5 rounded-full transition-colors"
                  :class="(activeImageIndex[index] ?? 0) === imgIdx ? 'bg-indigo-600' : 'bg-gray-300 dark:bg-gray-600 hover:bg-indigo-400'"
                />
              </div>
            </div>

            <div class="flex-1">
              <div class="flex items-start justify-between gap-4 mb-2">
                <h4 class="text-xl font-bold group-hover:text-indigo-600 dark:group-hover:text-indigo-400 transition-colors">
                  {{ project.title }}
                </h4>
                <a v-if="project.link" :href="project.link" target="_blank" class="shrink-0 text-xs text-indigo-600 dark:text-indigo-400 border border-indigo-200 dark:border-indigo-800 px-2 py-1 rounded hover:bg-indigo-50 dark:hover:bg-indigo-900/30 transition-colors">
                  Live →
                </a>
              </div>
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
        <p class="text-gray-600 dark:text-gray-400 mb-2 max-w-lg mx-auto text-lg">
          Tertarik untuk berdiskusi bagaimana saya dapat berkontribusi pada tim atau project Anda? Mari terhubung.
        </p>
        <p class="text-gray-500 dark:text-gray-500 mb-8 max-w-lg mx-auto">
          Saya sangat terbuka untuk kolaborasi project, baik dalam kapasitas profesional maupun freelance.
        </p>
        <div class="flex flex-col sm:flex-row justify-center gap-4">
          <a href="mailto:tobiasmikha33@gmail.com" class="bg-indigo-600 hover:bg-indigo-700 text-white px-8 py-3.5 rounded-lg font-medium transition-all shadow-lg shadow-indigo-200 dark:shadow-none hover:-translate-y-0.5">
            tobiasmikha33@gmail.com
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
