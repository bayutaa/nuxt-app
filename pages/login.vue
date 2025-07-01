<template>
  <div class="min-h-screen bg-gradient-to-br from-blue-50 to-indigo-100 flex items-center justify-center px-4">
    <div class="w-full max-w-md">
      <!-- Header -->
      <div class="text-center mb-8">
        <h1 class="text-2xl sm:text-3xl md:text-4xl font-bold text-gray-800 mb-2">
          Login
        </h1>
        <p class="text-gray-600">Silakan masuk ke akun Anda</p>
      </div>

      <!-- Login Form -->
      <div class="bg-white shadow-xl rounded-2xl p-8 border border-gray-100">
        <form @submit.prevent="handleSubmit" class="space-y-6">
          <!-- Success Message -->
          <div v-if="successMessage" class="bg-green-50 border border-green-200 text-green-600 px-4 py-3 rounded-lg text-sm">
            {{ successMessage }}
          </div>

          <!-- Demo Info -->
          <div class="bg-blue-50 border border-blue-200 text-blue-700 px-4 py-3 rounded-lg text-sm">
            <strong>Demo:</strong> Gunakan email: user@example.com, password: password123
          </div>

          <!-- Debug Info (hanya untuk development) -->
          <div v-if="isAuthenticated" class="bg-green-50 border border-green-200 text-green-700 px-4 py-3 rounded-lg text-sm">
            <strong>Status:</strong> Sudah login sebagai {{ user?.name }} ({{ user?.email }})
            <br>
            <button @click="logout" class="mt-2 text-xs bg-red-500 text-white px-2 py-1 rounded hover:bg-red-600">
              Logout
            </button>
          </div>

          <!-- Login History (untuk development) -->
          <div v-if="loginHistory.length > 0" class="bg-gray-50 border border-gray-200 text-gray-700 px-4 py-3 rounded-lg text-sm">
            <strong>Riwayat Login:</strong>
            <div class="mt-2 space-y-1">
              <div v-for="(entry, index) in loginHistory.slice(0, 3)" :key="index" class="text-xs">
                <span :class="entry.success ? 'text-green-600' : 'text-red-600'">
                  {{ entry.success ? '✓' : '✗' }}
                </span>
                {{ entry.email }} - {{ new Date(entry.loginTime).toLocaleString('id-ID') }}
              </div>
            </div>
          </div>

          <!-- Email Input -->
          <div>
            <label for="email" class="block text-sm font-medium text-gray-700 mb-2">
              Email <span class="text-red-500">*</span>
            </label>
            <input
              id="email"
              v-model="formData.email"
              type="email"
              placeholder="Masukkan email Anda"
              :class="[
                'w-full px-4 py-3 border rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-blue-500 outline-none transition-all duration-200 text-gray-900 placeholder-gray-500',
                errors.email ? 'border-red-300 focus:ring-red-500 focus:border-red-500' : 'border-gray-300'
              ]"
              :disabled="isLoading"
            />
            <p v-if="errors.email" class="mt-1 text-sm text-red-600">{{ errors.email }}</p>
          </div>

          <!-- Password Input -->
          <div>
            <label for="password" class="block text-sm font-medium text-gray-700 mb-2">
              Password <span class="text-red-500">*</span>
            </label>
            <div class="relative">
              <input
                id="password"
                v-model="formData.password"
                :type="showPassword ? 'text' : 'password'"
                placeholder="Masukkan password Anda"
                :class="[
                  'w-full px-4 py-3 pr-12 border rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-blue-500 outline-none transition-all duration-200 text-gray-900 placeholder-gray-500',
                  errors.password ? 'border-red-300 focus:ring-red-500 focus:border-red-500' : 'border-gray-300'
                ]"
                :disabled="isLoading"
              />
              <button
                type="button"
                @click="showPassword = !showPassword"
                class="absolute inset-y-0 right-0 pr-3 flex items-center text-gray-400 hover:text-gray-600"
                :disabled="isLoading"
              >
                <svg v-if="showPassword" class="h-5 w-5" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M13.875 18.825A10.05 10.05 0 0112 19c-4.478 0-8.268-2.943-9.543-7a9.97 9.97 0 011.563-3.029m5.858.908a3 3 0 114.243 4.243M9.878 9.878l4.242 4.242M9.878 9.878L8.464 8.464m1.414 1.414L15.12 15.12m-4.242-4.242L9.464 9.464" />
                </svg>
                <svg v-else class="h-5 w-5" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 12a3 3 0 11-6 0 3 3 0 016 0z" />
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M2.458 12C3.732 7.943 7.523 5 12 5c4.478 0 8.268 2.943 9.542 7-1.274 4.057-5.064 7-9.542 7-4.477 0-8.268-2.943-9.542-7z" />
                </svg>
              </button>
            </div>
            <p v-if="errors.password" class="mt-1 text-sm text-red-600">{{ errors.password }}</p>
          </div>

          <!-- Remember Me & Forgot Password -->
          <div class="flex items-center justify-between">
            <label class="flex items-center">
              <input
                v-model="formData.rememberMe"
                type="checkbox"
                class="w-4 h-4 text-blue-600 border-gray-300 rounded focus:ring-blue-500"
                :disabled="isLoading"
              />
              <span class="ml-2 text-sm text-gray-600">Ingat saya</span>
            </label>
            <NuxtLink to="/forgot-password" class="text-sm text-blue-600 hover:text-blue-800 font-medium">
              Lupa password?
            </NuxtLink>
          </div>

          <!-- Login Button -->
          <button
            type="submit"
            :disabled="isLoading"
            class="w-full bg-blue-600 text-white py-3 px-4 rounded-lg font-semibold hover:bg-blue-700 focus:ring-4 focus:ring-blue-200 focus:outline-none transition-all duration-200 disabled:opacity-50 disabled:cursor-not-allowed flex items-center justify-center"
          >
            <svg v-if="isLoading" class="animate-spin -ml-1 mr-3 h-5 w-5 text-white" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24">
              <circle class="opacity-25" cx="12" cy="12" r="10" stroke="currentColor" stroke-width="4"></circle>
              <path class="opacity-75" fill="currentColor" d="M4 12a8 8 0 018-8V0C5.373 0 0 5.373 0 12h4zm2 5.291A7.962 7.962 0 014 12H0c0 3.042 1.135 5.824 3 7.938l3-2.647z"></path>
            </svg>
            {{ isLoading ? 'Memproses...' : 'Masuk' }}
          </button>
        </form>

        <!-- Footer -->
        <div class="mt-6 text-center">
          <p class="text-gray-600 text-sm">
            Belum punya akun? 
            <NuxtLink to="/register" class="text-blue-600 hover:text-blue-800 font-medium ml-1">
              Daftar di sini
            </NuxtLink>
          </p>
        </div>
      </div>
    </div>

    <!-- Error Popup Modal -->
    <Teleport to="body">
      <div v-if="showErrorPopup" class="fixed inset-0 z-50 overflow-y-auto">
        <!-- Background overlay -->
        <div 
          class="fixed inset-0 bg-black bg-opacity-50 transition-opacity duration-300"
          @click="closeErrorPopup"
        ></div>

        <!-- Modal container -->
        <div class="flex items-center justify-center min-h-screen pt-4 px-4 pb-20 text-center">
          <!-- Modal panel -->
          <div 
            class="relative inline-block align-bottom bg-white rounded-lg text-left overflow-hidden shadow-xl transform transition-all duration-300 sm:my-8 sm:align-middle sm:max-w-lg sm:w-full mx-4"
            @click.stop
          >
            <div class="bg-white px-4 pt-5 pb-4 sm:p-6 sm:pb-4">
              <div class="sm:flex sm:items-start">
                <!-- Error Icon -->
                <div class="mx-auto flex-shrink-0 flex items-center justify-center h-12 w-12 rounded-full bg-red-100 sm:mx-0 sm:h-10 sm:w-10">
                  <svg class="h-6 w-6 text-red-600" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 9v2m0 4h.01m-6.938 4h13.856c1.54 0 2.502-1.667 1.732-2.5L13.732 4c-.77-.833-1.964-.833-2.732 0L3.732 16.5c-.77.833.192 2.5 1.732 2.5z" />
                  </svg>
                </div>
                
                <!-- Error Message -->
                <div class="mt-3 text-center sm:mt-0 sm:ml-4 sm:text-left">
                  <h3 class="text-lg leading-6 font-medium text-gray-900">
                    Login Gagal
                  </h3>
                  <div class="mt-2">
                    <p class="text-sm text-gray-500">
                      {{ errorMessage }}
                    </p>
                  </div>
                </div>
              </div>
            </div>
            
            <!-- Button actions -->
            <div class="bg-gray-50 px-4 py-3 sm:px-6 sm:flex sm:flex-row-reverse">
              <button
                type="button"
                @click="closeErrorPopup"
                class="w-full inline-flex justify-center rounded-md border border-transparent shadow-sm px-4 py-2 bg-red-600 text-base font-medium text-white hover:bg-red-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-red-500 sm:ml-3 sm:w-auto sm:text-sm transition-colors duration-200"
              >
                Tutup
              </button>
              <button
                type="button"
                @click="resetForm"
                class="mt-3 w-full inline-flex justify-center rounded-md border border-gray-300 shadow-sm px-4 py-2 bg-white text-base font-medium text-gray-700 hover:bg-gray-50 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-blue-500 sm:mt-0 sm:ml-3 sm:w-auto sm:text-sm transition-colors duration-200"
              >
                Coba Lagi
              </button>
            </div>
          </div>
        </div>
      </div>
    </Teleport>
  </div>
</template>

<script setup>
// Meta tags untuk SEO
useHead({
  title: 'Login - Masuk ke Akun Anda',
  meta: [
    { name: 'description', content: 'Halaman login untuk masuk ke akun Anda' }
  ]
})

// Reactive data
const formData = ref({
  email: '',
  password: '',
  rememberMe: false
})

const errors = ref({})
const isLoading = ref(false)
const showPassword = ref(false)
const successMessage = ref('')

// Popup error states
const showErrorPopup = ref(false)
const errorMessage = ref('')

// Authentication state using useState
const user = useState('auth.user', () => null)
const isAuthenticated = useState('auth.isAuthenticated', () => false)
const authToken = useState('auth.token', () => null)

// Login history state
const loginHistory = useState('auth.loginHistory', () => [])

// Validasi form
const validateForm = () => {
  const newErrors = {}

  // Validasi email
  if (!formData.value.email.trim()) {
    newErrors.email = 'Email wajib diisi'
  } else if (!/^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(formData.value.email)) {
    newErrors.email = 'Format email tidak valid'
  }

  // Validasi password
  if (!formData.value.password.trim()) {
    newErrors.password = 'Password wajib diisi'
  } else if (formData.value.password.length < 6) {
    newErrors.password = 'Password minimal 6 karakter'
  }

  return newErrors
}

// Clear error saat user mengetik
watch(() => formData.value.email, () => {
  if (errors.value.email) {
    errors.value.email = ''
  }
})

watch(() => formData.value.password, () => {
  if (errors.value.password) {
    errors.value.password = ''
  }
})

// Functions untuk popup
const showError = (message) => {
  errorMessage.value = message
  showErrorPopup.value = true
  console.log('Showing error popup:', message) // Debug log
}

const closeErrorPopup = () => {
  showErrorPopup.value = false
  errorMessage.value = ''
  console.log('Closing error popup') // Debug log
}

const resetForm = () => {
  formData.value.email = ''
  formData.value.password = ''
  formData.value.rememberMe = false
  errors.value = {}
  closeErrorPopup()
}

// Authentication functions
const setAuthData = (userData, token) => {
  user.value = userData
  authToken.value = token
  isAuthenticated.value = true
  
  // Simpan ke localStorage jika remember me dicentang
  if (formData.value.rememberMe) {
    if (process.client) {
      localStorage.setItem('authToken', token)
      localStorage.setItem('userData', JSON.stringify(userData))
    }
  }
  
  // Simpan ke session storage
  if (process.client) {
    sessionStorage.setItem('currentSession', JSON.stringify({
      user: userData,
      token: token,
      loginTime: new Date().toISOString()
    }))
  }
  
  // Update login history
  const newLoginEntry = {
    email: userData.email,
    name: userData.name,
    loginTime: new Date().toISOString(),
    success: true
  }
  
  loginHistory.value = [newLoginEntry, ...loginHistory.value.slice(0, 4)] // Keep last 5 entries
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

// Check existing auth on component mount
const checkExistingAuth = () => {
  if (process.client) {
    const savedToken = localStorage.getItem('authToken')
    const savedUserData = localStorage.getItem('userData')
    const sessionData = sessionStorage.getItem('currentSession')
    
    if (savedToken && savedUserData) {
      try {
        const userData = JSON.parse(savedUserData)
        setAuthData(userData, savedToken)
        console.log('Restored auth from localStorage:', userData)
      } catch (error) {
        console.error('Error parsing saved user data:', error)
        clearAuthData()
      }
    } else if (sessionData) {
      try {
        const session = JSON.parse(sessionData)
        setAuthData(session.user, session.token)
        console.log('Restored auth from sessionStorage:', session.user)
      } catch (error) {
        console.error('Error parsing session data:', error)
        clearAuthData()
      }
    }
  }
}

// Handle form submission
const handleSubmit = async () => {
  const validationErrors = validateForm()
  
  if (Object.keys(validationErrors).length > 0) {
    errors.value = validationErrors
    return
  }

  isLoading.value = true
  errors.value = {}
  successMessage.value = ''
  
  try {
    // Simulasi delay loading
    await new Promise(resolve => setTimeout(resolve, 1500))
    
    // Simulasi validasi login
    if (formData.value.email === 'user@example.com' && formData.value.password === 'password123') {
      // Login berhasil - buat user data
      const userData = {
        id: 1,
        email: formData.value.email,
        name: 'Demo User',
        role: 'user',
        avatar: null,
        preferences: {
          theme: 'light',
          language: 'id'
        }
      }
      
      const token = 'demo-jwt-token-' + Date.now()
      
      // Set auth data menggunakan useState
      setAuthData(userData, token)
      
      successMessage.value = `Selamat datang, ${userData.name}! Login berhasil. Mengalihkan ke homepage...`
      
      // Log successful login
      console.log('Login successful:', {
        user: userData,
        token: token,
        rememberMe: formData.value.rememberMe
      })
      
      // Redirect ke homepage setelah 2 detik
      setTimeout(() => {
        navigateTo('/homepage') // Uncomment ini untuk redirect nyata
        console.log('Redirect to homepage with user:', user.value)
      }, 2000)
    } else {
      // Login gagal - log failed attempt
      const failedLoginEntry = {
        email: formData.value.email,
        loginTime: new Date().toISOString(),
        success: false,
        error: 'Invalid credentials'
      }
      
      loginHistory.value = [failedLoginEntry, ...loginHistory.value.slice(0, 4)]
      
      throw new Error('Email atau password salah. Gunakan: user@example.com / password123')
    }
  } catch (error) {
    // Tampilkan popup error
    showError(error.message || 'Terjadi kesalahan saat login. Silakan coba lagi.')
  } finally {
    isLoading.value = false
  }
}

// Close popup dengan ESC key
const handleKeydown = (event) => {
  if (event.key === 'Escape' && showErrorPopup.value) {
    closeErrorPopup()
  }
}

// Add event listener untuk ESC key
onMounted(() => {
  document.addEventListener('keydown', handleKeydown)
  
  // Check for existing authentication
  checkExistingAuth()
  
  // Redirect if already authenticated
  if (isAuthenticated.value) {
    console.log('User already authenticated, redirecting...', user.value)
    navigateTo('/homepage') // Uncomment untuk redirect otomatis
  }
})

onUnmounted(() => {
  document.removeEventListener('keydown', handleKeydown)
})

// Logout function (untuk digunakan di komponen lain)
const logout = () => {
  clearAuthData()
  console.log('User logged out')
  // navigateTo('/login') // Redirect ke login page
}

// Expose logout function globally
if (process.client) {
  window.logout = logout
}
</script>

<style scoped>
/* Animasi untuk popup */
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.3s ease;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}

/* Animasi untuk modal */
.modal-enter-active,
.modal-leave-active {
  transition: all 0.3s ease;
}

.modal-enter-from,
.modal-leave-to {
  opacity: 0;
  transform: scale(0.9);
}
</style>