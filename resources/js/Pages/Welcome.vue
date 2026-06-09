<script setup>
import { Head, Link } from '@inertiajs/vue3';
import { ref, onMounted } from 'vue';

// Props (bisa dihapus jika tidak diperlukan)
defineProps({
    canLogin: {
        type: Boolean,
    },
    canRegister: {
        type: Boolean,
    },
    laravelVersion: {
        type: String,
        required: true,
    },
    phpVersion: {
        type: String,
        required: true,
    },
});

// Reactive state
const show = ref(false);

// Lifecycle hook equivalent to useEffect
onMounted(() => {
    const timer = setTimeout(() => {
        show.value = true;
    }, 100);

    return () => clearTimeout(timer);
});
</script>

<template>
    <Head title="Welcome" />
    
    <!-- Main Container -->
    <div
        class="relative text-black w-full h-screen flex justify-center items-center overflow-hidden"
    >
        <!-- Background Image -->
        <img
            src="assets/img/back_home2.svg"
            alt="background"
            class="absolute top-0 left-0 w-full h-full object-cover z-0 transition-opacity duration-1000 ease-in-out"
            :class="show ? 'opacity-100' : 'opacity-0'"
        />

        <!-- Main Content -->
        <div
            class="relative z-10 backdrop-blur-md rounded-3xl px-8 py-10 sm:px-14 sm:py-14 md:px-20 md:py-16 text-center transform transition-all duration-700 ease-out"
            :class="show ? 'scale-100 opacity-100 translate-y-0' : 'scale-95 opacity-0 translate-y-10'"
        >
            <div class="grid grid-cols-2 gap-4 sm:gap-5">
                
                <!-- Header -->
                <div class="font-bold text-black mb-4 sm:mb-5 col-span-2">
                    <p class="text-lg sm:text-xl md:text-2xl">Selamat Datang di</p>
                    <p class="text-2xl sm:text-3xl md:text-4xl font-bold">ASKES</p>
                    <p class="text-lg sm:text-xl md:text-2xl">(Asrama & Kesehatan)</p>
                    <p class="text-lg sm:text-xl md:text-2xl">Daarel Hasanah</p>
                </div>

                <!-- Logo -->
                <div class="flex justify-center col-span-2">
                    <img
                        src="assets/img/logo-dh.png"
                        alt="logo-dh"
                        class="w-24 sm:w-26 md:w-36 h-auto transition-all duration-700"
                        :class="show ? 'opacity-100 scale-100' : 'opacity-0 scale-75'"
                    />
                </div>

                <!-- Buttons -->
                <div class="col-span-2 mt-4 sm:mt-5">
                    <div class="grid grid-cols-2">
                        <Link
                            :href="route('register')"
                            class="bg-white hover:bg-gray-300 transition-all duration-500 py-2 sm:py-3 text-base sm:text-lg font-bold flex justify-center items-center rounded-l-full transform transition-all duration-700 ease-out"
                            :class="show ? 'translate-y-0 opacity-100' : 'translate-y-10 opacity-0'"
                        >
                            Daftar
                        </Link>
                        <Link
                            :href="route('login')"
                            class="bg-white hover:bg-gray-300 transition-all duration-500 py-2 sm:py-3 text-base sm:text-lg font-bold flex justify-center items-center rounded-r-full border-l border-gray-300 delay-100 transform transition-all duration-700 ease-out"
                            :class="show ? 'translate-y-0 opacity-100' : 'translate-y-10 opacity-0'"
                        >
                            Masuk
                        </Link>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>