<template>
  <div class="min-h-screen bg-gradient-to-br from-blue-50 to-indigo-100 flex-1 flex flex-col">

    <!-- Main Content -->
    <main class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-12">
      <div class="text-center mb-12">
        <h2 class="text-4xl font-bold text-gray-900 mb-4">Layanan Medis Kami</h2>
        <p class="text-xl text-gray-600 max-w-3xl mx-auto">
          Temukan berbagai layanan kesehatan berkualitas tinggi dengan teknologi modern dan tenaga medis berpengalaman
        </p>
      </div>

      <!-- Pinterest-style Grid -->
      <div class="columns-1 md:columns-2 lg:columns-3 xl:columns-4 gap-6 space-y-6">
        
        <!-- Kardiologi - Tall Card -->
        <div class="break-inside-avoid bg-white rounded-3xl shadow-xl overflow-hidden hover:shadow-2xl transition-all duration-300 transform hover:-translate-y-2 group">
          <div class="h-64 bg-gradient-to-br from-red-500 to-pink-600 relative overflow-hidden">
            <div class="absolute inset-0 bg-black/20"></div>
            <div class="absolute inset-0 flex items-center justify-center">
              <img src="/images/cardiology.png" alt="Kardiologi Icon" class="w-24 h-24 opacity-80 group-hover:scale-110 transition-transform duration-300 object-contain">
            </div>
            <div class="absolute top-4 right-4">
              <span class="bg-white bg-opacity-20 text-black text-xs px-3 py-1 rounded-full font-medium">Spesialis</span>
            </div>
          </div>
          <div class="p-6">
            <h3 class="text-2xl font-bold text-gray-900 mb-3">Kardiologi</h3>
            <p class="text-gray-600 mb-4">Pelayanan jantung dan pembuluh darah dengan teknologi terdepan. EKG, Ekokardiografi, dan Kateterisasi Jantung.</p>
            <div class="flex items-center justify-between">
              <div class="flex items-center space-x-2">
                <div class="w-8 h-8 bg-red-100 rounded-full flex items-center justify-center">
                  <svg class="w-4 h-4 text-red-600" fill="currentColor" viewBox="0 0 20 20">
                    <path d="M9 12l2 2 4-4m6 2a9 9 0 11-18 0 9 9 0 0118 0z"></path>
                  </svg>
                </div>
                <span class="text-sm text-gray-600">24/7 Available</span>
              </div>
              <button class="bg-red-500 text-white px-4 py-2 rounded-xl hover:bg-red-600 transition-colors">
                Info Detail
              </button>
            </div>
          </div>
        </div>

        <!-- IGD - Compact Card -->
        <div class="break-inside-avoid bg-white rounded-3xl shadow-xl overflow-hidden hover:shadow-2xl transition-all duration-300 transform hover:-translate-y-2 group">
          <div class="h-48 bg-gradient-to-br from-red-600 to-orange-500 relative overflow-hidden">
            <div class="absolute inset-0 bg-black/50"></div>
            <div class="absolute inset-0 flex items-center justify-center">
              <img src="/images/IGD.png" alt="IGD Icon" class="w-24 h-24 opacity-80 group-hover:scale-110 transition-transform duration-300 object-contain">
            </div>
            <div class="absolute top-4 left-4">
              <span class="bg-red-600 text-white text-xs px-3 py-1 rounded-full font-bold animate-pulse">URGENT</span>
            </div>
          </div>
          <div class="p-5">
            <h3 class="text-xl font-bold text-gray-900 mb-2">Instalasi Gawat Darurat</h3>
            <p class="text-gray-600 text-sm mb-3">Layanan darurat 24 jam dengan tim medis siaga dan ambulance.</p>
            <div class="bg-red-50 p-3 rounded-xl">
              <p class="text-red-700 text-sm font-medium">🚨 Hotline: 021-1234-5678</p>
            </div>
          </div>
        </div>

        <!-- Neurologi - Medium Card -->
        <div class="break-inside-avoid bg-white rounded-3xl shadow-xl overflow-hidden hover:shadow-2xl transition-all duration-300 transform hover:-translate-y-2 group">
          <div class="h-56 bg-gradient-to-br from-purple-600 to-blue-600 relative overflow-hidden">
            <div class="absolute inset-0 bg-black/20"></div>
            <div class="absolute inset-0 flex items-center justify-center">
              <img src="/images/neurology.png" alt="Neurology Icon" class="w-24 h-24 opacity-80 group-hover:scale-110 transition-transform duration-300 object-contain">
            </div>
          </div>
          <div class="p-6">
            <h3 class="text-xl font-bold text-gray-900 mb-3">Neurologi</h3>
            <p class="text-gray-600 mb-4">Spesialis saraf dan otak dengan pemeriksaan EEG, MRI, dan CT Scan neurologis.</p>
            <div class="space-y-2">
              <div class="flex items-center space-x-2">
                <div class="w-2 h-2 bg-purple-500 rounded-full"></div>
                <span class="text-sm text-gray-600">Stroke Center</span>
              </div>
              <div class="flex items-center space-x-2">
                <div class="w-2 h-2 bg-blue-500 rounded-full"></div>
                <span class="text-sm text-gray-600">Epilepsy Care</span>
              </div>
            </div>
          </div>
        </div>

        <!-- Farmasi - Wide Card -->
        <div class="break-inside-avoid bg-white rounded-3xl shadow-xl overflow-hidden hover:shadow-2xl transition-all duration-300 transform hover:-translate-y-2 group">
          <div class="h-40 bg-gradient-to-r from-green-500 to-teal-500 relative overflow-hidden">
            <div class="absolute inset-0 bg-black/20"></div>
            <div class="absolute inset-0 flex items-center justify-center">
               <img src="/images/pharmacy.png" alt="Pharmacy Icon" class="w-24 h-24 opacity-80 group-hover:scale-110 transition-transform duration-300 object-contain">
            </div>
          </div>
          <div class="p-5">
            <h3 class="text-xl font-bold text-gray-900 mb-2">Farmasi</h3>
            <p class="text-gray-600 text-sm mb-4">Apotek lengkap dengan obat-obatan berkualitas dan konsultasi farmasis berpengalaman.</p>
            <div class="grid grid-cols-2 gap-3">
              <div class="bg-green-50 p-3 rounded-xl text-center">
                <div class="text-green-600 font-bold text-lg">500+</div>
                <div class="text-green-700 text-xs">Jenis Obat</div>
              </div>
              <div class="bg-teal-50 p-3 rounded-xl text-center">
                <div class="text-teal-600 font-bold text-lg">24/7</div>
                <div class="text-teal-700 text-xs">Buka</div>
              </div>
            </div>
          </div>
        </div>

        <!-- Radiologi - Tall Card -->
        <div class="break-inside-avoid bg-white rounded-3xl shadow-xl overflow-hidden hover:shadow-2xl transition-all duration-300 transform hover:-translate-y-2 group">
          <div class="h-72 bg-gradient-to-br from-indigo-600 to-purple-700 relative overflow-hidden">
            <div class="absolute inset-0 bg-black/20"></div>
            <div class="absolute inset-0 flex items-center justify-center">
              <img src="/images/radiology.png" alt="Radiology Icon" class="w-24 h-24 opacity-80 group-hover:scale-110 transition-transform duration-300 object-contain">
            </div>
            <div class="absolute bottom-4 left-4 right-4">
              <div class="bg-white bg-opacity-20 backdrop-blur-sm rounded-xl p-3">
                <p class="text-white text-sm font-medium">Teknologi Imaging Terbaru</p>
              </div>
            </div>
          </div>
          <div class="p-6">
            <h3 class="text-2xl font-bold text-gray-900 mb-3">Radiologi</h3>
            <p class="text-gray-600 mb-4">Pemeriksaan radiologi lengkap dengan teknologi digital terdepan untuk diagnosis yang akurat.</p>
            <div class="space-y-3">
              <div class="flex items-center justify-between p-3 bg-indigo-50 rounded-xl">
                <span class="text-indigo-700 font-medium">X-Ray Digital</span>
                <svg class="w-5 h-5 text-indigo-600" fill="currentColor" viewBox="0 0 20 20">
                  <path fill-rule="evenodd" d="M16.707 5.293a1 1 0 010 1.414l-8 8a1 1 0 01-1.414 0l-4-4a1 1 0 011.414-1.414L8 12.586l7.293-7.293a1 1 0 011.414 0z" clip-rule="evenodd"></path>
                </svg>
              </div>
              <div class="flex items-center justify-between p-3 bg-purple-50 rounded-xl">
                <span class="text-purple-700 font-medium">CT Scan & MRI</span>
                <svg class="w-5 h-5 text-purple-600" fill="currentColor" viewBox="0 0 20 20">
                  <path fill-rule="evenodd" d="M16.707 5.293a1 1 0 010 1.414l-8 8a1 1 0 01-1.414 0l-4-4a1 1 0 011.414-1.414L8 12.586l7.293-7.293a1 1 0 011.414 0z" clip-rule="evenodd"></path>
                </svg>
              </div>
            </div>
          </div>
        </div>

        <!-- Medical Checkup - Medium Card -->
        <div class="break-inside-avoid bg-white rounded-3xl shadow-xl overflow-hidden hover:shadow-2xl transition-all duration-300 transform hover:-translate-y-2 group">
          <div class="h-52 bg-gradient-to-br from-emerald-500 to-cyan-500 relative overflow-hidden">
            <div class="absolute inset-0 bg-black/20"></div>
            <div class="absolute inset-0 flex items-center justify-center">
               <img src="/images/mcu.png" alt="Medical Checkup Icon" class="w-24 h-24 opacity-80 group-hover:scale-110 transition-transform duration-300 object-contain">
            </div>
            <div class="absolute top-4 right-4">
              <span class="bg-emerald-600 text-white text-xs px-3 py-1 rounded-full font-medium">Popular</span>
            </div>
          </div>
          <div class="p-6">
            <h3 class="text-xl font-bold text-gray-900 mb-3">Medical Check Up</h3>
            <p class="text-gray-600 mb-4">Paket pemeriksaan kesehatan menyeluruh untuk deteksi dini berbagai penyakit.</p>
            <div class="bg-gradient-to-r from-emerald-50 to-cyan-50 p-4 rounded-xl">
              <div class="flex items-center justify-between mb-2">
                <span class="text-emerald-700 font-semibold">Paket Basic</span>
                <span class="text-cyan-700 font-bold">Rp 250K</span>
              </div>
              <p class="text-emerald-600 text-sm">Lab lengkap + konsultasi dokter</p>
            </div>
          </div>
        </div>

        <!-- Tambahan - Orthopedi -->
        <div class="break-inside-avoid bg-white rounded-3xl shadow-xl overflow-hidden hover:shadow-2xl transition-all duration-300 transform hover:-translate-y-2 group">
          <div class="h-44 bg-gradient-to-br from-amber-500 to-orange-600 relative overflow-hidden">
            <div class="absolute inset-0 bg-black/20"></div>
            <div class="absolute inset-0 flex items-center justify-center">
               <img src="/images/orthopedi.png" alt="Orthopedi Icon" class="w-24 h-24 opacity-80 group-hover:scale-110 transition-transform duration-300 object-contain">
            </div>
          </div>
          <div class="p-5">
            <h3 class="text-xl font-bold text-gray-900 mb-2">Orthopedi</h3>
            <p class="text-gray-600 text-sm mb-3">Spesialis tulang dan sendi dengan teknologi arthroscopy modern.</p>
            <div class="flex items-center space-x-4 text-sm">
              <div class="flex items-center space-x-1">
                <div class="w-2 h-2 bg-amber-500 rounded-full"></div>
                <span class="text-gray-600">Fisioterapi</span>
              </div>
              <div class="flex items-center space-x-1">
                <div class="w-2 h-2 bg-orange-500 rounded-full"></div>
                <span class="text-gray-600">Operasi</span>
              </div>
            </div>
          </div>
        </div>

      </div>

      <!-- CTA Section -->
      <div class="mt-16 text-center">
        <div class="bg-gradient-to-r from-blue-600 to-green-600 rounded-3xl p-8 text-white">
          <h3 class="text-3xl font-bold mb-4">Butuh Konsultasi?</h3>
          <p class="text-blue-100 mb-6 max-w-2xl mx-auto">
            Tim medis kami siap membantu Anda 24/7. Hubungi kami untuk konsultasi atau appointment.
          </p>
          <div class="flex flex-col sm:flex-row gap-4 justify-center">
            <button class="bg-white text-blue-600 px-8 py-3 rounded-xl font-semibold hover:bg-blue-50 transition-colors">
              Buat Appointment
            </button>
            <button class="border-2 border-white text-white px-8 py-3 rounded-xl font-semibold hover:bg-white hover:text-blue-600 transition-colors">
              Hubungi Kami
            </button>
          </div>
        </div>
      </div>
    </main>
  </div>
</template>

<script setup>
// Nuxt.js composition API setup
definePageMeta({
  title: 'Layanan Medis - RS MediCare',
  description: 'Temukan berbagai layanan kesehatan berkualitas tinggi di RS MediCare'
})

// Head configuration for SEO
useHead({
  title: 'Layanan Medis - RS MediCare',
  meta: [
    { name: 'description', content: 'Layanan kesehatan terpercaya dengan teknologi modern dan tenaga medis berpengalaman' },
    { name: 'keywords', content: 'rumah sakit, layanan medis, kardiologi, neurologi, radiologi, IGD, medical checkup' }
  ]
})
</script>

<style scoped>
/* Custom animations and effects */
.group:hover .group-hover\:scale-110 {
  transform: scale(1.1);
}

/* Masonry layout improvements */
.columns-1 {
  column-count: 1;
}

@media (min-width: 768px) {
  .md\:columns-2 {
    column-count: 2;
  }
}

@media (min-width: 1024px) {
  .lg\:columns-3 {
    column-count: 3;
  }
}

@media (min-width: 1280px) {
  .xl\:columns-4 {
    column-count: 4;
  }
}

/* Prevent card breaking */
.break-inside-avoid {
  break-inside: avoid;
  page-break-inside: avoid;
}

/* Smooth transitions */
* {
  transition-property: transform, box-shadow, background-color, border-color, color;
  transition-duration: 300ms;
  transition-timing-function: cubic-bezier(0.4, 0, 0.2, 1);
}
</style>