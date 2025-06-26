<template>
  <div class="min-h-screen bg-gradient-to-br from-blue-50 to-indigo-100">
    <!-- Header -->
    <header class="bg-white shadow-lg">
      <div class="container mx-auto px-6 py-4">
        <h1 class="text-3xl font-bold text-indigo-800 text-center">
          Perjalanan Sejarah RSUD Dr. Saiful Anwar
        </h1>
        <p class="text-center text-gray-600 mt-2">
          Jelajahi momen-momen bersejarah tentang RSUD Dr. Saiful Anwar
        </p>
      </div>
    </header>

    <!-- Main Content -->
    <main class="container mx-auto px-6 py-8">

      <!-- History Display -->
      <div class="bg-white rounded-2xl shadow-xl overflow-hidden">
        <div class="grid lg:grid-cols-2 gap-0">
          <!-- Image Slider Section -->
          <div class="relative bg-gray-900">
            <div class="aspect-[4/3] relative overflow-hidden">
              <!-- Main Image -->
              <img
                :src="currentStory.image"
                :alt="currentStory.title"
                class="w-full h-full object-cover transition-all duration-500"
              />
              
              <!-- Image Overlay -->
              <div class="absolute inset-0 bg-gradient-to-t from-black/50 to-transparent"></div>
              
              <!-- Image Title -->
              <div class="absolute bottom-4 left-4 right-4">
                <h3 class="text-white text-xl font-bold mb-2">
                  {{ currentStory.title }}
                </h3>
                <p class="text-white/80 text-sm">
                  {{ currentStory.date }}
                </p>
              </div>
            </div>

            <!-- Navigation Arrows -->
            <button
              @click="previousStory"
              class="absolute left-4 top-1/2 transform -translate-y-1/2 bg-white/20 hover:bg-white/30 text-white p-3 rounded-full transition-all duration-300 backdrop-blur-sm"
            >
              <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 19l-7-7 7-7"></path>
              </svg>
            </button>
            
            <button
              @click="nextStory"
              class="absolute right-4 top-1/2 transform -translate-y-1/2 bg-white/20 hover:bg-white/30 text-white p-3 rounded-full transition-all duration-300 backdrop-blur-sm"
            >
              <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5l7 7-7 7"></path>
              </svg>
            </button>

            <!-- Dots Indicator -->
            <div class="absolute bottom-4 left-1/2 transform -translate-x-1/2 flex space-x-2">
              <button
                v-for="(story, index) in allStories"
                :key="index"
                @click="currentStoryIndex = index"
                :class="[
                  'w-3 h-3 rounded-full transition-all duration-300',
                  currentStoryIndex === index
                    ? 'bg-white'
                    : 'bg-white/50 hover:bg-white/70'
                ]"
              ></button>
            </div>
          </div>

          <!-- Text Content Section -->
          <div class="p-8 lg:p-12">
            <div class="h-full flex flex-col">
              <!-- Period Title -->
              <div class="mb-6">
                <span class="inline-block px-4 py-2 bg-indigo-100 text-indigo-800 rounded-full text-sm font-semibold mb-4">
                  {{ currentStory.period }}
                </span>
                <h2 class="text-2xl lg:text-3xl font-bold text-gray-800 mb-2">
                  {{ currentStory.title }}
                </h2>
                <p class="text-indigo-600 font-semibold">
                  {{ currentStory.date }}
                </p>
              </div>

              <!-- Story Content -->
              <div class="flex-1">
                <p class="text-gray-700 leading-relaxed text-lg mb-6">
                  {{ currentStory.description }}
                </p>
                
                <!-- Key Points -->
                <div class="space-y-3">
                  <h4 class="font-semibold text-gray-800 mb-3">Poin Penting:</h4>
                  <div
                    v-for="(point, index) in currentStory.keyPoints"
                    :key="index"
                    class="flex items-start space-x-3"
                  >
                    <div class="w-2 h-2 bg-indigo-500 rounded-full mt-2 flex-shrink-0"></div>
                    <p class="text-gray-600">{{ point }}</p>
                  </div>
                </div>
              </div>

              <!-- Story Counter -->
              <div class="mt-8 pt-6 border-t border-gray-200">
                <div class="flex justify-between items-center text-sm text-gray-500">
                  <span>
                    {{ currentStoryIndex + 1 }} dari {{ allStories.length }} cerita
                  </span>
                  <span>
                    Periode: {{ currentStory.period }}
                  </span>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>

      <!-- Timeline Navigation -->
      <div class="mt-12">
        <h3 class="text-xl font-bold text-center text-gray-800 mb-6">
          Timeline Sejarah
        </h3>
        <div class="flex justify-center">
          <div class="flex space-x-4 overflow-x-auto pb-4">
            <div
              v-for="(story, index) in allStories"
              :key="index"
              @click="currentStoryIndex = index"
              :class="[
                'flex-shrink-0 w-24 h-24 rounded-lg cursor-pointer transition-all duration-300 border-4 relative',
                currentStoryIndex === index
                  ? 'border-indigo-500 transform scale-110'
                  : 'border-transparent hover:border-indigo-300'
              ]"
            >
              <img
                :src="story.image"
                :alt="story.title"
                class="w-full h-full object-cover rounded-lg"
              />
              <!-- Period badge on thumbnail -->
              <div class="absolute -top-2 -right-2 bg-indigo-600 text-white text-xs px-2 py-1 rounded-full">
                {{ story.period.charAt(0) }}
              </div>
            </div>
          </div>
        </div>
      </div>
    </main>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue'

// Reactive state
const currentStoryIndex = ref(0)

// Sample history data - flattened into single array
const allStories = ref([
  {
    title: "RS Celaket",
    period: "Sebelum Perang Dunia II",
    date: "< 1942",
    image: "/images/rssa 1.jpg",
    description: "Sebelum Perang Dunia II, RSUD Dr. Saiful Anwar (dulu RS Celaket) adalah rumah sakit militer KNIL, lalu diambil alih Jepang dan tetap dipakai sebagai rumah sakit militer.",
    keyPoints: [
      "Saat perang kemerdekaan, RS Celaket jadi rumah sakit tentara",
      "RS Sukun melayani masyarakat umum di bawah Kotapraja Malang",
      "Tahun 1947, RS Sukun diambil alih tentara karena lebih strategis",
      "RS Sukun jadi rumah sakit militer, RS Celaket jadi rumah sakit umum"
    ]
  },
  {
    title: "Diambil Alih Jepang",
    period: "Pendudukan Jepang",
    date: "1942 - 1945",
    image: "/images/rssa 2.jpg",
    description: "Pada masa pendudukan Jepang, Rumah Sakit Celaket diambil alih oleh pihak militer Jepang dan terus difungsikan sebagai rumah sakit militer untuk mendukung kebutuhan medis pasukan mereka. ",
    keyPoints: [
      "Rumah sakit dikuasai militer Jepang",
      "Kekurangan tenaga medis dan obat-obatan",
      "Penggunaan sistem kerja paksa (romusha)",
      "Perubahan sistem dan bahasa"
    ]
  },
  {
    title: "Kerjasama STKM-RS Celaket",
    period: "Setelah Kemerdekaan",
    date: "1963",
    image: "/images/rssa 3.jpg",
    description: "Pada 14 September 1963, STKM dibuka oleh Yayasan Perguruan Tinggi Jawa Timur/IDI dan menjadikan RS Celaket sebagai tempat praktik, yang diresmikan lewat kerja sama pada 23 Agustus 1969.",
    keyPoints: [
        "STKM didirikan pada 14 September 1963",
        "Pembukaan Sekolah Tinggi Kedokteran Malang (STKM)",
        "RS Celaket jadi Rumah Sakit Pendidikan",
        "Cikal bakal Fakultas Kedokteran Universitas Brawijaya (FKUB)"
    ]
  },
  {
    title: "Resmi menjadi RSUD Dr. Saiful Anwar",
    period: "Setelah Kemerdekaan",
    date: "1979",
    image: "/images/rssa 4.jpg",
    description: "Pada tanggal 12 November 1979, oleh Gubernur Kepala Daerah Tingkat I Jawa Timur, Rumah Sakit Celaket diresmikan sebagai Rumah Sakit Umum Daerah Dr. Saiful Anwar.",
    keyPoints: [
      "Perubahan Nama Resmi",
      "Penghormatan kepada Tokoh Kesehatan",
      "Status sebagai RS Pemerintah Provinsi",
      "Tonggak Sejarah Modernisasi"
    ]
  }
])

// Computed properties
const currentStory = computed(() => allStories.value[currentStoryIndex.value])

// Methods
const nextStory = () => {
  if (currentStoryIndex.value < allStories.value.length - 1) {
    currentStoryIndex.value++
  } else {
    currentStoryIndex.value = 0
  }
}

const previousStory = () => {
  if (currentStoryIndex.value > 0) {
    currentStoryIndex.value--
  } else {
    currentStoryIndex.value = allStories.value.length - 1
  }
}

// Watch for period changes to reset story index - removed since no more periods

// Auto-slide functionality (optional)
let autoSlideInterval = null

const startAutoSlide = () => {
  autoSlideInterval = setInterval(() => {
    nextStory()
  }, 5000) // Change slide every 5 seconds
}

const stopAutoSlide = () => {
  if (autoSlideInterval) {
    clearInterval(autoSlideInterval)
    autoSlideInterval = null
  }
}

// Lifecycle
onMounted(() => {
  startAutoSlide()
})

onUnmounted(() => {
  stopAutoSlide()
})
</script>

<style scoped>
/* Custom scrollbar for timeline */
::-webkit-scrollbar {
  height: 8px;
}

::-webkit-scrollbar-track {
  background: #f1f1f1;
  border-radius: 4px;
}

::-webkit-scrollbar-thumb {
  background: #4f46e5;
  border-radius: 4px;
}

::-webkit-scrollbar-thumb:hover {
  background: #3730a3;
}

/* Smooth transitions */
* {
  transition: all 0.3s ease;
}

/* Image fade effect */
img {
  transition: opacity 0.5s ease, transform 0.5s ease;
}

/* Hover effects */
.hover\:scale-105:hover {
  transform: scale(1.05);
}

/* Focus styles for accessibility */
button:focus {
  outline: 2px solid #4f46e5;
  outline-offset: 2px;
}
</style>