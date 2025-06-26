<template>
  <main class="min-h-screen bg-gradient-to-br from-blue-50 to-indigo-100 flex-1 flex flex-col">
    <!-- Hero Section with Background Image -->
    <div class="relative h-[80vh] bg-cover bg-center bg-no-repeat" style="background-image: url('/images/medical-bg.png');">
      <!-- Background Overlay -->
      <div class="absolute inset-0 bg-black/50"></div>
      
      <!-- Content Container -->
      <div class="relative z-10 flex flex-col items-center justify-center h-full px-4 py-12">
        <!-- Welcome Section -->
        <div class="w-full max-w-6xl mx-auto mb-12">
          <!-- Title Section -->
          <div class="text-center mb-8">
            <h2 class="text-3xl sm:text-4xl md:text-5xl font-bold text-white mb-4">
              RSUD Dr. Saiful Anwar
            </h2>
            <p class="text-lg sm:text-xl text-blue-100 max-w-2xl mx-auto mb-2">
              Kami menyediakan Berbagai Layanan Unggulan Untuk Meningkatkan Kesehatan Anda
            </p>
          </div>

          <!-- Search Section -->
          <div class="bg-white/95 backdrop-blur-sm rounded-lg shadow-lg p-6 max-w-2xl mx-auto">
            <h3 class="text-xl font-semibold text-gray-800 mb-4 text-center">
              Cari Layanan atau Informasi
            </h3>
            <div class="relative">
              <input 
                type="text" 
                placeholder="Masukkan kata kunci pencarian..." 
                class="w-full px-4 py-3 pr-12 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500 focus:border-transparent"
              />
              <button 
                class="absolute right-2 top-1/2 transform -translate-y-1/2 bg-blue-600 text-white p-2 rounded-md hover:bg-blue-700 transition-colors"
              >
                <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M21 21l-6-6m2-5a7 7 0 11-14 0 7 7 0 0114 0z"></path>
                </svg>
              </button>
            </div>
            
            <!-- Search Suggestions -->
            <div class="flex flex-wrap gap-2 mt-4">
              <span class="text-sm text-gray-600">Pencarian populer:</span>
            </div>
          </div>
        </div>
      </div>
    </div>

    <!-- Content Section -->
    <div class="bg-gradient-to-br from-blue-50 to-indigo-100 px-4 py-12">
      <!-- Description Section -->
      <div class="text-center max-w-3xl mx-auto mb-12">
        <h3 class="text-2xl sm:text-3xl font-bold text-gray-800 mb-6">
          Tentang Website Ini
        </h3>
        <p class="text-gray-600 text-base sm:text-lg leading-relaxed mb-8">
          RSUD Dr. Saiful Anwar Malang merupakan rumah sakit rujukan utama di Jawa Timur yang 
          berkomitmen memberikan pelayanan kesehatan terbaik. Dengan teknologi medis terdepan 
          dan tenaga medis yang berpengalaman, kami siap melayani kebutuhan kesehatan masyarakat 
          dengan standar internasional.
        </p>
        
        <!-- Call to Action Buttons -->
        <div class="flex flex-col sm:flex-row gap-4 justify-center">
          <button 
            class="bg-blue-600 text-white px-8 py-3 rounded-lg font-semibold hover:bg-blue-700 transition-all duration-200 shadow-lg hover:shadow-xl"
          >
            Jelajahi Galeri
          </button>
          <button 
            class="bg-white text-blue-600 px-8 py-3 rounded-lg font-semibold border-2 border-blue-600 hover:bg-blue-50 transition-all duration-200"
          >
            Pelajari Lebih Lanjut
          </button>
        </div>
      </div>

      <!-- Features Grid -->
      <div class="w-full max-w-6xl mx-auto grid grid-cols-1 md:grid-cols-3 gap-8">
        <!-- Feature 1 -->
        <div class="bg-white rounded-lg p-6 shadow-lg hover:shadow-xl transition-shadow duration-200">
          <div class="w-12 h-12 bg-blue-100 rounded-lg flex items-center justify-center mb-4">
            <svg class="w-6 h-6 text-blue-600" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 21V5a2 2 0 00-2-2H7a2 2 0 00-2 2v16m14 0h2m-2 0h-5m-9 0H3m2 0h5M9 7h1m-1 4h1m4-4h1m-1 4h1m-5 10v-5a1 1 0 011-1h2a1 1 0 011 1v5m-4 0h4"></path>
            </svg>
          </div>
          <h4 class="text-xl font-semibold text-gray-800 mb-2">Layanan Rawat Inap</h4>
          <p class="text-gray-600">Fasilitas rawat inap dengan standar internasional dan perawatan 24 jam</p>
        </div>

        <!-- Feature 2 -->
        <div class="bg-white rounded-lg p-6 shadow-lg hover:shadow-xl transition-shadow duration-200">
          <div class="w-12 h-12 bg-green-100 rounded-lg flex items-center justify-center mb-4">
            <svg class="w-6 h-6 text-green-600" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4.318 6.318a4.5 4.5 0 000 6.364L12 20.364l7.682-7.682a4.5 4.5 0 00-6.364-6.364L12 7.636l-1.318-1.318a4.5 4.5 0 00-6.364 0z"></path>
            </svg>
          </div>
          <h4 class="text-xl font-semibold text-gray-800 mb-2">Layanan Darurat</h4>
          <p class="text-gray-600">Unit Gawat Darurat siap melayani 24 jam dengan tim medis berpengalaman</p>
        </div>

        <!-- Feature 3 -->
        <div class="bg-white rounded-lg p-6 shadow-lg hover:shadow-xl transition-shadow duration-200">
          <div class="w-12 h-12 bg-purple-100 rounded-lg flex items-center justify-center mb-4">
            <svg class="w-6 h-6 text-purple-600" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 12h6m-6 4h6m2 5H7a2 2 0 01-2-2V5a2 2 0 012-2h5.586a1 1 0 01.707.293l5.414 5.414a1 1 0 01.293.707V19a2 2 0 01-2 2z"></path>
            </svg>
          </div>
          <h4 class="text-xl font-semibold text-gray-800 mb-2">Pendaftaran Online</h4>
          <p class="text-gray-600">Kemudahan mendaftar secara online untuk berbagai layanan medis</p>
        </div>
      </div>
    </div>
  </main>
</template>

<style scoped>
/* Custom styles untuk memastikan background image responsif */
@media (max-width: 768px) {
  .bg-cover {
    background-size: cover;
    background-position: center;
  }
}
</style>