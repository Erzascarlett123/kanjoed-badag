<script>
	import Guru from './../components/guru.svelte';
  import Navbar from './../components/navbar.svelte';
  import { page } from '$app/stores'; // Mengimpor store `page` dari SvelteKit
  import { goto } from '$app/navigation';
  import { onMount } from 'svelte';
  import "../app.css";

  let showNavbar = true;

  let user;



  // Memantau perubahan pada path untuk menyembunyikan navbar pada halaman tertentu
  $: {
    const hideNavbarOnPaths = ['/dashboard%20guru', '/login', '/', '/dashboard%20murid/jiko%20shoukai'];
    showNavbar = !hideNavbarOnPaths.includes($page.url.pathname);
  }
</script>

<head>
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css" />
</head>

<!-- Menampilkan navbar hanya jika `showNavbar` true -->
{#if showNavbar}
  {#if $page.url.pathname.includes('guru')}
    <Guru />
  {:else}
    <Navbar />
  {/if}
{/if}

<slot />
