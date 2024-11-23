<script setup>
    import { RouterLink } from 'vue-router';
    

</script>

<template>
    <section class="flex flex-col justify-center items-center gap-3 mt-9">
        <i class="pi pi-exclamation-triangle text-yellow-500 text-7xl"></i>
        <h1 class="text-3xl font-bold">404 Not Found!</h1>
        <p class="font-semibold">This page does not exist...</p>
        <RouterLink to="/" class="bg-green-600 text-white px-2 py-1 rounded-md">Go Back</RouterLink>
    </section>
</template>