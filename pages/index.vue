<template>
  <!-- Main Content -->
    <main class="flex-1 flex flex-col items-center justify-center px-4 py-12">
      <!-- Welcome Section -->
      <div class="text-center mb-12">
        <h2 class="text-3xl sm:text-4xl md:text-5xl font-bold text-gray-800 mb-4">
          Selamat Datang
        </h2>
        <p class="text-lg sm:text-xl text-gray-600 max-w-2xl mx-auto">
          Website ini menampilkan pemandangan indah dan konten menarik untuk pengunjung
        </p>
      </div>

      <!-- Main Image Section -->
      <div class="w-full max-w-4xl mx-auto mb-12">
        <div class="relative overflow-hidden rounded-2xl shadow-2xl">
          <!-- Local Image - Ganti 'my-landscape.jpg' dengan nama file gambar kamu -->
          <img 
            src="https://rsusaifulanwar.jatimprov.go.id/wp-content/uploads/2016/09/rssa.jpg" 
            alt="Rumah Sakit Saiful Anwar" 
            class="w-full h-64 sm:h-80 md:h-96 lg:h-[500px] object-cover"
          />
          <!-- Image Overlay -->
          <div class="absolute inset-0 bg-black/40 flex items-center justify-center">
            <div class="text-center text-white">
              <h3 class="text-2xl sm:text-3xl md:text-4xl font-bold mb-2">
                Pemandangan Indah
              </h3>
              <p class="text-sm sm:text-base md:text-lg opacity-90">
                Nikmati keindahan alam yang menakjubkan
              </p>
            </div>
          </div>
        </div>
      </div>

      <!-- Description Section -->
      <div class="text-center max-w-3xl mx-auto mb-12">
        <h3 class="text-2xl sm:text-3xl font-bold text-gray-800 mb-6">
          Tentang Website Ini
        </h3>
        <p class="text-gray-600 text-base sm:text-lg leading-relaxed mb-8">
          Website ini dibuat untuk menampilkan koleksi gambar pemandangan yang indah dan memberikan 
          inspirasi kepada pengunjung. Setiap gambar dipilih dengan cermat untuk memberikan 
          pengalaman visual yang menyenangkan.
        </p>
        
        <!-- Call to Action Buttons -->
        <div class="flex flex-col sm:flex-row gap-4 justify-center">
          <button class="bg-blue-600 text-white px-8 py-3 rounded-lg font-semibold hover:bg-blue-700 transition-all duration-200 shadow-lg hover:shadow-xl">
            Jelajahi Galeri
          </button>
          <button class="bg-white text-blue-600 px-8 py-3 rounded-lg font-semibold border-2 border-blue-600 hover:bg-blue-50 transition-all duration-200">
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
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 16l4.586-4.586a2 2 0 012.828 0L16 16m-2-2l1.586-1.586a2 2 0 012.828 0L20 14m-6-6h.01M6 20h12a2 2 0 002-2V6a2 2 0 00-2-2H6a2 2 0 00-2 2v12a2 2 0 002 2z"></path>
            </svg>
          </div>
          <h4 class="text-xl font-semibold text-gray-800 mb-2">Galeri Foto</h4>
          <p class="text-gray-600">Koleksi foto pemandangan berkualitas tinggi dari berbagai lokasi indah</p>
        </div>

        <!-- Feature 2 -->
        <div class="bg-white rounded-lg p-6 shadow-lg hover:shadow-xl transition-shadow duration-200">
          <div class="w-12 h-12 bg-green-100 rounded-lg flex items-center justify-center mb-4">
            <svg class="w-6 h-6 text-green-600" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17.657 16.657L13.414 20.9a1.998 1.998 0 01-2.827 0l-4.244-4.243a8 8 0 1111.314 0z"></path>
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 11a3 3 0 11-6 0 3 3 0 016 0z"></path>
            </svg>
          </div>
          <h4 class="text-xl font-semibold text-gray-800 mb-2">Lokasi Menarik</h4>
          <p class="text-gray-600">Informasi lokasi dan tips untuk mengunjungi tempat-tempat indah</p>
        </div>

        <!-- Feature 3 -->
        <div class="bg-white rounded-lg p-6 shadow-lg hover:shadow-xl transition-shadow duration-200">
          <div class="w-12 h-12 bg-purple-100 rounded-lg flex items-center justify-center mb-4">
            <svg class="w-6 h-6 text-purple-600" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 6.253v13m0-13C10.832 5.477 9.246 5 7.5 5S4.168 5.477 3 6.253v13C4.168 18.477 5.754 18 7.5 18s3.332.477 4.5 1.253m0-13C13.168 5.477 14.754 5 16.5 5c1.746 0 3.332.477 4.5 1.253v13C19.832 18.477 18.246 18 16.5 18c-1.746 0-3.332.477-4.5 1.253"></path>
            </svg>
          </div>
          <h4 class="text-xl font-semibold text-gray-800 mb-2">Panduan Travel</h4>
          <p class="text-gray-600">Panduan lengkap untuk merencanakan perjalanan ke destinasi impian</p>
        </div>
      </div>
    </main>
</template>