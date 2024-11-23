<script setup>
import { reactive, defineProps, onMounted } from "vue";
import { RouterLink } from "vue-router";
import axios from "axios";
import PulseLoader from 'vue-spinner/src/PulseLoader.vue';
import JobListingCard from "./JobListingCard.vue";

const state = reactive({
    jobs: [],
    isLoading: true
})
defineProps({
    limit: Number,
    showButton: {
        type: Boolean,
        default: true
    }
})

onMounted(async () => {
    try {
        const response = await axios.get('http://localhost:8080/jobs')
        state.jobs = response.data
    } catch (error) {
        console.error("Error loading jobs...", error)
    } finally {
        state.isLoading = false
    }
})
</script>

<template>
    <section class="bg-blue-50 p-10 lg:px-28">
        <div>
            <h2 class="text-center text-3xl text-green-500 mb-6 font-black">Browse Jobs</h2>
            <div v-if="state.isLoading" class="text-center">
                <PulseLoader />
            </div>
            <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
                <JobListingCard v-for="job in state.jobs.slice(0, limit || state.jobs.length)" :key="job.id"
                    :job="job" />
            </div>
        </div>
    </section>
    <div class="flex justify-center">
        <RouterLink v-if="showButton" to="/jobs" class="block my-8 bg-black text-white py-3 w-48 text-center rounded-md hover:opacity-80">
            View All
        </RouterLink>
    </div>
</template>