<script setup>
    import { defineProps } from 'vue';
    defineProps({
        // data: {
        //     type: Array,
        //     default: []
        // }
        bg: {
            type: String,
            default: 'bg-gray-200'
        }
    })
</script>

<template>
    <div :class="`${bg} p-3 rounded-md flex flex-col gap-2 shadow lg:w-full`">
        <slot></slot>
    </div>
</template>