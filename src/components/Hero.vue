<script setup>
    import { defineProps } from 'vue';

    defineProps({
        title: {
            type: String,
            default: 'Become a Vue Dev'
        },
        subtitle: {
            type: String,
            default: "Find the Vue job that fits your skills and needs"
        }
    })
</script>

<template>
    <div class="flex-[0_0_30%] bg-green-700 text-white flex flex-col items-center justify-center gap-2">
        <h1 class="text-4xl lg:text-5xl font-black">{{title}}</h1>
        <p>{{subtitle}}</p>
    </div>
</template>
