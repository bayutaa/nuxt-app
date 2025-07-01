<template>
    <div>
        Ini adalah homepage setelah Login
    </div>
</template>

<script setup>

const user = useState('auth.user')
const isAuthenticated = useState('auth.isAuthenticated')

onMounted(() => {
  document.addEventListener('keydown', handleKeydown)
  
  // Check for existing authentication
  checkExistingAuth()
  
  // Redirect if already authenticated
  if (!isAuthenticated.value) {
    console.log('User already authenticated, redirecting...', user.value)
    router.push('/') // Uncomment untuk redirect otomatis
  }
})

</script>