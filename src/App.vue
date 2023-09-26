<script setup lang="ts">
import { RouterView } from 'vue-router'
import Header from './layout/Header.vue'
</script>

<template>
  <Header />
  <main>
    <RouterView />
  </main>
</template>