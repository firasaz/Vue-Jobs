<script setup>
  import { RouterView } from 'vue-router';
import Navbar from './components/Navbar.vue';
  import MainLayout from './layouts/MainLayout.vue';
</script>

<template>
  <MainLayout>
    <Navbar />
    <hr />
    <RouterView />
  </MainLayout>
</template>
