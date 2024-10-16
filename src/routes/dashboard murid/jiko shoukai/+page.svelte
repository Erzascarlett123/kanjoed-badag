<script lang="ts">
    import { userName, userClass } from '../../../stores/user'; // Import store
    import { goto } from '$app/navigation';

    let name = '';
    let selectedClass = '';

    let classes = ['Kelas X', 'Kelas XI', 'Kelas XII'];

    function handleSubmit() {
        if (name && selectedClass) {
            userName.set(name); // Update store dengan nama
            userClass.set(selectedClass); // Update store dengan kelas
            goto('/dashboard murid'); // Arahkan ke halaman berikutnya
        } else {
            alert('Mohon isi semua field');
        }
    }
</script>

<main class="min-h-screen flex items-center justify-center bg-gray-100">
    <div class="bg-white p-8 rounded shadow-md w-full max-w-md">
        <h1 class="text-2xl font-bold text-center mb-6">Isi Form</h1>
        
        <form on:submit|preventDefault={handleSubmit}>
            <div class="mb-4">
                <label class="block text-gray-700 text-sm font-bold mb-2" for="name">Nama</label>
                <input
                    id="name"
                    type="text"
                    bind:value={name}
                    class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
                    placeholder="Masukkan nama"
                    required
                />
            </div>

            <div class="mb-6">
                <label class="block text-gray-700 text-sm font-bold mb-2" for="class">Kelas</label>
                <select
                    id="class"
                    bind:value={selectedClass}
                    class="block appearance-none w-full bg-white border border-gray-400 hover:border-gray-500 px-4 py-2 pr-8 rounded shadow leading-tight focus:outline-none focus:shadow-outline"
                    required
                >
                    <option value="" disabled>Pilih kelas</option>
                    {#each classes as kelas} 
                        <option value={kelas}>{kelas}</option>
                    {/each}
                </select>
            </div>

            <div class="flex items-center justify-between">
                <button
                    type="submit"
                    class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded focus:outline-none focus:shadow-outline"
                >
                    Submit
                </button>
            </div>
        </form>
    </div>
</main>
