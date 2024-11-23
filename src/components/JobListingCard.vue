<script setup>
import { defineProps, computed, ref } from 'vue';
import { RouterLink } from 'vue-router';

const props = defineProps({
    job: {
        type: Object,
        default: {}
    },
})

const showFullDescr = ref(false)
const toggleShowFullDescr = () => {
    showFullDescr.value = !showFullDescr.value
}
const trunctuatedDescr = computed(() => {
    let descr = props.job.description
    if (!showFullDescr.value) {
        descr = descr.substring(0, 90) + '...'
    }
    return descr
})


</script>

<template>
    <div class="bg-white p-3 rounded-lg shadow flex flex-col justify-between">
        <div>
            <p class="text-sm opacity-80">{{ job.type }}</p>
            <h3 class="text-xl font-bold">{{ job.title }}</h3>
            <p class="mt-3 mb-0">{{ trunctuatedDescr }}</p>
            <button class="text-sm mt-0 mb-3 rounded-xl text-blue-500" @click="toggleShowFullDescr">
                {{ showFullDescr ? 'less' : 'more' }}
            </button>
        </div>
        <div>
            <p class="text-green-500 font-semibold">{{ job.salary }} / Year</p>
            <hr class="my-2" />
            <div class="flex gap-2 justify-between">
                <div class="text-orange-700 font-semibold flex gap-1 items-center">
                    <i class="pi pi-map-marker"></i>
                    <span>{{ job.location }}</span>
                </div>
                <RouterLink
                    :to="`/job/${job.id}`"
                    class="bg-green-500 hover:bg-green-600 text-white text-center rounded py-1 px-3"
                >
                    Read More
                </RouterLink>
            </div>
        </div>
    </div>
</template>