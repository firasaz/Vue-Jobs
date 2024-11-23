<script setup>
    import { RouterLink, useRoute } from 'vue-router';
    import logo from '../assets/vue.svg'
    
    const isActive = (routePath) => {
        const currentRoute = useRoute(routePath)
        return currentRoute.path === routePath
    }
</script>

<template>
    <nav class="flex justify-between items-center bg-green-700 px-20 lg:px-32 py-2 gap-2 text-white">
        <img :src="logo" width="40" class="bg-white rounded-full p-1" />
        <div class="flex gap-3">
            <RouterLink
            to="/"
            :class="['text-white', 'hover:bg-green-900', 'rounded-md', 'px-2', 'py-1', isActive('/') ? 'bg-green-900' : '']"
            >
                Home
            </RouterLink>
            <RouterLink
            to="/jobs"
            :class="['text-white', 'hover:bg-green-900', 'rounded-md', 'px-2', 'py-1', isActive('/jobs') ? 'bg-green-900' : '']"
            >
                Jobs
            </RouterLink>
            <RouterLink
            to="/jobs/add"
            :class="['text-white', 'hover:bg-green-900', 'rounded-md', 'px-2', 'py-1', isActive('/jobs/add') ? 'bg-green-900' : '']"
            >
                Add Job
            </RouterLink>
        </div>
    </nav>
</template>