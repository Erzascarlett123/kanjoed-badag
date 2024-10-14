<script>
  import { goto } from '$app/navigation';
  import { onMount } from 'svelte';

  let isMounted = false;
  let isLogin = true;
  let errorMessage = '';
  let successMessage = '';  

  const handleGoogleLogin = async () => {
      try {
          // Tambahkan logika login Google di sini
          goto('/');
      } catch (error) {
          console.error('Error logging in with Google:', error);
      }
  };

  onMount(() => {
      isMounted = true; // Mengontrol tampilan ketika komponen dimuat
  });

  const toggleForm = () => {
      isLogin = !isLogin;
      errorMessage = '';
      successMessage = '';
  };
</script>

<div class="flex items-center justify-center min-h-screen bg-gradient-to-r from-green-400 via-teal-500 to-green-600">
  <div class={`w-full max-w-xs p-6 space-y-8 bg-white rounded-xl shadow-lg ${isMounted ? 'fade-in' : 'hidden'}`}>
      <h2 class="text-2xl font-bold text-center text-gray-700">Login</h2>
      <p class="text-xs text-center text-gray-500">Login dengan akun Google Anda</p>

      <div class="mt-4">
          <button on:click={handleGoogleLogin} class="w-full py-2 text-white bg-red-500 rounded-lg hover:bg-red-600 transition-all duration-200 ease-in-out">
              Login dengan Google
          </button>
      </div>
  </div>
</div>

<style>
  .fade-in {
      animation: fadeInUp 1s ease;
  }
  @keyframes fadeInUp {
      from {
          opacity: 0;
          transform: translateY(20px);
      }
      to {
          opacity: 1;
          transform: translateY(0);
      }
  }
</style>
