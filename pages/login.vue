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
        <form class="space-y-6">
          <!-- Email Input -->
          <div>
            <label for="email" class="block text-sm font-medium text-gray-700 mb-2">
              Email
            </label>
            <input
              id="email"
              type="email"
              placeholder="Masukkan email Anda"
              class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-blue-500 outline-none transition-all duration-200 text-gray-900 placeholder-gray-500"
            />
          </div>

          <!-- Password Input -->
          <div>
            <label for="password" class="block text-sm font-medium text-gray-700 mb-2">
              Password
            </label>
            <input
              id="password"
              type="password"
              placeholder="Masukkan password Anda"
              class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-blue-500 outline-none transition-all duration-200 text-gray-900 placeholder-gray-500"
            />
          </div>

          <!-- Remember Me & Forgot Password -->
          <div class="flex items-center justify-between">
            <label class="flex items-center">
              <input
                type="checkbox"
                class="w-4 h-4 text-blue-600 border-gray-300 rounded focus:ring-blue-500"
              />
              <span class="ml-2 text-sm text-gray-600">Ingat saya</span>
            </label>
            <a href="#" class="text-sm text-blue-600 hover:text-blue-800 font-medium">
              Lupa password?
            </a>
          </div>

          <!-- Buttons -->
          <div class="space-y-3">
            <!-- Login Button -->
            <button
              type="submit"
              class="w-full bg-blue-600 text-white py-3 px-4 rounded-lg font-semibold hover:bg-blue-700 focus:ring-4 focus:ring-blue-200 focus:outline-none transition-all duration-200"
            >
              Masuk
            </button>
          </div>
        </form>

        <!-- Footer -->
        <div class="mt-6 text-center">
          <p class="text-gray-600 text-sm">
            Belum punya akun? 
            <a href="#" class="text-blue-600 hover:text-blue-800 font-medium ml-1">
              Daftar di sini
            </a>
          </p>
        </div>
      </div>
    </div>
  </div>
</template>