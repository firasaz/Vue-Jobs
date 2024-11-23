<script setup>
import { onMounted, reactive } from 'vue';
import { RouterLink, useRoute } from 'vue-router';
import router from '@/router'
import axios from 'axios';
import { useToast } from 'vue-toastification';

    const route = useRoute()
    const jobId = route.params.jobId
    const toast = useToast()

    const state = reactive({
        job: {},
        isLoading: true
    })
    const handleDeleteJob = async () => {
        try {
            const confirm = window.confirm('Are you sure you want to delete this job?')
            if(confirm) {
                await axios.delete(`/api/jobs/${jobId}`)
                toast.success('Job Deleted Successfully')
                router.push('/jobs')
            }
        } catch (err) {
            toast.error("Job Couldn't Be Deleted :(")
            console.err('error deleting job', err)
        }
    }
    
    onMounted(async () => {
        try {
            const response = await axios.get(`/api/jobs/${jobId}`)
            state.job = response.data
        } catch (err) {
            console.error('error fetching job details', err)
        } finally {
            state.isLoading = false
        }
    })
</script>

<template>
    <section class="px-20 py-8 h-full bg-green-100 flex gap-3">
        <div class="flex flex-col gap-3 w-3/4">
            <div class="bg-white rounded shadow p-5 flex flex-col gap-2">
                <p>{{state.job.type}}</p>
                <h1 class="text-3xl font-extrabold">{{state.job.title}}</h1>
                <div class="flex items-center gap-1 text-orange-700">
                    <i class="pi pi-map-marker"></i>
                    <p>{{ state.job.location }}</p>
                </div>
            </div>
            <div class="bg-white rounded shadow p-5 flex flex-col gap-3">
                <div>
                    <h4 class="text-lg text-green-900 font-bold">Job Description</h4>
                    <p>{{ state.job.description }}</p>
                </div>
                <div>
                    <h4 class="text-lg text-green-900 font-bold">Salary</h4>
                    <p>{{ state.job.salary }} / Year</p>
                </div>
            </div>
        </div>

        <div class="flex flex-col gap-3 lg:w-1/4">
            <div class="bg-white p-3 rounded shadow flex flex-col gap-3">
                <h4 class="font-extrabold">Company Info</h4>
                <div>
                    <h3 class="text-2xl mb-1">{{ state.job.company?.name }}</h3>
                    <p>{{ state.job.company?.description }}</p>
                </div>
                <hr />
                <div>
                    <h2>Contact Email:</h2>
                    <p class="p-2 bg-green-100 font-bold overflow-hidden text-ellipsis">{{ state.job.company?.contactEmail }}</p>
                    <h2>Contact Phone:</h2>
                    <p class="p-2 bg-green-100 font-bold">{{ state.job.company?.contactPhone }}</p>
                </div>
            </div>
            <div class="bg-white p-3 shadow rounded">
                <h1 class="font-bold text-xl">Manage Job</h1>
                <RouterLink 
                    :to="`/jobs/edit/${state.job.id}`" 
                    class="block bg-green-500 text-center text-white w-full mt-3 py-1 rounded-full font-bold"
                >
                    Edit Job
                </RouterLink>
                <button 
                    @click="handleDeleteJob"
                    class="block bg-red-500 text-center text-white w-full mt-3 py-1 rounded-full font-bold"
                >
                    Delete Job
                </button>
            </div>
        </div>
    </section>
</template>