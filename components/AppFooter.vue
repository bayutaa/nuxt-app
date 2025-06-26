<template>
  <footer class="bg-gray-900 text-white">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-12">
      <div class="grid md:grid-cols-4 gap-8">
        <div>
          <h3 class="text-lg font-semibold mb-4">Alamat</h3>
          <p class="text-gray-400">
            Jl. Jaksa Agung Suprapto No.2, Klojen, Kec. Klojen, Kota Malang, Jawa Timur 65112
          </p>
        </div>
        <div>
          <h4 class="font-semibold mb-4">Product</h4>
          <ul class="space-y-2 text-gray-400">
            <li><NuxtLink to="/healthservices" class="hover:text-white transition">Health Services</NuxtLink></li>
            <li><a href="#" class="hover:text-white transition">Features</a></li>
            <li><a href="#" class="hover:text-white transition">Pricing</a></li>
          </ul>
        </div>
        <div>
          <h4 class="font-semibold mb-4">Company</h4>
          <ul class="space-y-2 text-gray-400">
            <li><NuxtLink to="/about" class="hover:text-white transition">About</NuxtLink></li>
            <li><a href="#" class="hover:text-white transition">Blog</a></li>
            <li><NuxtLink to="/contact" class="hover:text-white transition">Contact</NuxtLink></li>
          </ul>
        </div>
        <div>
          <h4 class="font-semibold mb-4">Follow Us</h4>
          <div class="flex space-x-4">
            <img 
              @click="openInstagramApp"
              src="/images/instagram.png" 
              alt="Instagram Logo" 
              class="w-7 h-7 object-contain cursor-pointer hover:opacity-80 transition-opacity duration-200"
            />
            <img 
              @click="openTwitterApp"
              src="/images/twitter3.png" 
              alt="Twitter Logo" 
              class="w-7 h-7 object-contain cursor-pointer hover:opacity-80 transition-opacity duration-200"
            />
          </div>
        </div>
      </div>
      <div class="border-t border-gray-800 mt-12 pt-8 text-center text-gray-400">
        <p>&copy; 2025 RSSA. All rights reserved.</p>
      </div>
    </div>
  </footer>
</template>

<script setup>
const openInstagramApp = () => {
  const instagramUrl = `https://www.instagram.com/rssaifulanwar/?hl=en`
  
  // Buka Instagram di tab baru
  window.open(instagramUrl, '_blank')
}

const openTwitterApp = () => {
  const twitterUrl = 'https://x.com/rsudsaifulanwar?lang=en'

  // Buka Twitter di tab baru
  window.open(twitterUrl, '_blank')
}

</script>