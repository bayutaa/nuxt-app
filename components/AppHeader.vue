<template>
  <nav class="bg-white shadow-sm sticky top-0 z-50">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <div class="flex justify-between items-center h-16">
        <div class="flex items-center">
          <NuxtLink to="/" class="flex items-center">
            <img 
              src="/images/image icon rssa.png" 
              alt="Logo" 
              class="h-13 w-auto"
            >
          </NuxtLink>
        </div>
        <div class="hidden md:block">
          <div class="ml-10 flex items-baseline space-x-4">
            <NuxtLink 
              to="/" 
              class="text-gray-600 hover:text-gray-900 px-3 py-2 rounded-md text-sm font-medium transition"
              :class="{ 'text-indigo-600 font-semibold': $route.path === '/' }"
            >
              Home
            </NuxtLink>
            <NuxtLink 
              to="/about" 
              class="text-gray-600 hover:text-gray-900 px-3 py-2 rounded-md text-sm font-medium transition"
              :class="{ 'text-indigo-600 font-semibold': $route.path === '/about' }"
            >
              About
            </NuxtLink>
            <NuxtLink 
              to="/healthservices" 
              class="text-gray-600 hover:text-gray-900 px-3 py-2 rounded-md text-sm font-medium transition"
              :class="{ 'text-indigo-600 font-semibold': $route.path === '/healthservices' }"
            >
              Health Services
            </NuxtLink>
            <NuxtLink 
              to="/contact" 
              class="text-gray-600 hover:text-gray-900 px-3 py-2 rounded-md text-sm font-medium transition"
              :class="{ 'text-indigo-600 font-semibold': $route.path === '/contact' }"
            >
              Contact
            </NuxtLink>
            <NuxtLink 
              to="/login" 
              class="text-gray-600 hover:text-gray-900 px-3 py-2 rounded-md text-sm font-medium transition"
              :class="{ 'text-indigo-600 font-semibold': $route.path === '/login' }" v-if="!user"
            >
              Login
            </NuxtLink>
            <NuxtLink 
              to="/" 
              class="text-gray-600 hover:text-gray-900 px-3 py-2 rounded-md text-sm font-medium transition"
              :class="{ 'text-indigo-600 font-semibold': $route.path === '/' }" v-if="user" @click="logout()"
            >
              Logout
            </NuxtLink>
          </div>
        </div>
        
        <!-- Mobile menu button -->
        <div class="md:hidden">
          <button @click="mobileMenuOpen = !mobileMenuOpen" class="text-gray-600">
            <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16"></path>
            </svg>
          </button>
        </div>
      </div>
      
      <!-- Mobile menu -->
      <div v-show="mobileMenuOpen" class="md:hidden">
        <div class="px-2 pt-2 pb-3 space-y-1 sm:px-3 bg-white border-t">
          <NuxtLink to="/" class="block px-3 py-2 text-gray-600 hover:text-gray-900">Home</NuxtLink>
          <NuxtLink to="/" class="block px-3 py-2 text-gray-600 hover:text-gray-900">About</NuxtLink>
          <NuxtLink to="/" class="block px-3 py-2 text-gray-600 hover:text-gray-900">Services</NuxtLink>
          <NuxtLink to="/" class="block px-3 py-2 text-gray-600 hover:text-gray-900">Contact</NuxtLink>
        </div>
      </div>
    </div>
  </nav>
</template>

<script setup>
const mobileMenuOpen = ref(false)

// const statusLogin = ref(false); 

const user = useState('auth.user')
const isAuthenticated = useState('auth.isAuthenticated')

if (isAuthenticated.value) {
  console.log('User:', user.value.name)
}

const logout = () => {
  clearAuthData();
  navigateTo('/login');
}

const clearAuthData = () => {
  user.value = null
  authToken.value = null
  isAuthenticated.value = false
  
  if (process.client) {
    localStorage.removeItem('authToken')
    localStorage.removeItem('userData')
    sessionStorage.removeItem('currentSession')
  }
}

</script>