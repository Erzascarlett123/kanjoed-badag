<script lang="ts">
  import { goto } from '$app/navigation'; // Pastikan untuk menggunakan ini jika menggunakan routing
</script>

<nav class="bg-blue-700 text-white shadow-lg py-4 px-8">
    <div class="container mx-auto flex justify-between items-center">
      <div class="text-2xl font-bold">Mba Icha Class</div>
      <div>Nama Murid: Reza</div>
      <button class="bg-red-500 hover:bg-red-700 transition-colors px-4 py-2 rounded-md"   on:click={() => goto('/login')}>Logout</button>
    </div>
  </nav>