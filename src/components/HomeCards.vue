<script setup>
import { RouterLink } from 'vue-router';
import Card from './Card.vue';

const data = {
    title: 'For Employers',
    subtitle: 'List your job to find the perfect developer for the role'
}
</script>

<template>
    <div class="px-10 py-8 lg:px-28 lg:py-12 flex flex-col lg:flex-row lg:justify-center gap-3">
        <Card>
            <h4 class="text-xl font-bold">For Developers</h4>
            <p class="font-semibold">Browser our Vue jobs and start your career today</p>
            <RouterLink to="/jobs" class="rounded-lg bg-black hover:bg-stone-800 text-white px-2 py-1 w-fit">Browse Jobs</RouterLink>
        </Card>
        <Card bg="bg-green-100">
            <h4 class="text-xl font-bold">For Developers</h4>
            <p class="font-semibold">Browser our Vue jobs and start your career today</p>
            <RouterLink to="/jobs/add" class="rounded-lg bg-green-500 hover:bg-green-600 text-white px-2 py-1 w-fit">Add Jobs</RouterLink>
        </Card>
    </div>
</template>