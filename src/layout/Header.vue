<script setup lang="ts">
import { RouterLink } from 'vue-router'
</script>

<template>
    <header class="bg-blue-600 py-5">
        <nav class="flex gap-6 text-2xl text-white justify-center">
            <RouterLink to="/">Home</RouterLink>
            <RouterLink to="/about">About</RouterLink>
        </nav>
    </header>
</template>