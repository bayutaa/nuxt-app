<template>
  <div class="min-h-screen bg-gradient-to-br from-blue-50 to-indigo-100 py-30 px-4 sm:px-6 lg:px-8">
    <div class="max-w-md mx-auto bg-white rounded-lg shadow-md p-8">
      <!-- Header -->
      <div class="text-center mb-8">
        <h1 class="text-2xl font-bold text-gray-900 mb-2">Contact Us</h1>
        <p class="text-gray-600">Hubungi kami melalui WhatsApp</p>
      </div>

      <!-- WhatsApp Contact Card -->
      <div class="bg-green-50 border border-green-200 rounded-lg p-6 mb-6">
        <div class="flex items-center justify-center mb-4">
          <!-- WhatsApp Logo Image -->
          <img 
            src="/images/whatsapp.png" 
            alt="WhatsApp Logo" 
            class="w-16 h-16 object-contain"
          />
        </div>

        <div class="text-center">
          <h3 class="text-lg font-semibold text-gray-900 mb-2">WhatsApp</h3>
          <p class="text-gray-600 mb-4">Chat langsung dengan kami</p>
          
          <!-- Chat Button -->
          <button 
            @click="openWhatsApp"
            class="w-full bg-green-500 hover:bg-green-600 text-white font-medium py-3 px-6 rounded-lg transition-colors duration-200 flex items-center justify-center space-x-2">
            <span>Chat Sekarang</span>
          </button>
        </div>
      </div>

      <!-- Contact Info -->
      <div class="text-center text-sm text-gray-500">
        <p>Kami siap membantu Anda</p>
        <p>Respon cepat dalam 5 menit</p>
      </div>
    </div>
  </div>
</template>

<script setup>
// Ganti nomor ini dengan nomor WhatsApp bisnis Anda
const whatsappNumber = '6282215778959' // Format: 62 (kode negara Indonesia) + nomor tanpa 0 di depan
const defaultMessage = 'Halo, saya ingin bertanya mengenai layanan Anda.'

const openWhatsApp = () => {
  const encodedMessage = encodeURIComponent(defaultMessage)
  const whatsappUrl = `https://wa.me/${whatsappNumber}?text=${encodedMessage}`
  
  // Buka WhatsApp di tab baru
  window.open(whatsappUrl, '_blank')
}

</script>