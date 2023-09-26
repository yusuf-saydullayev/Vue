<script setup lang="ts">
import type { listUser } from '@/types/User';
type ComponentProps = {
    users: listUser,
    deleteUser: (id: number) => void
}
defineProps<ComponentProps>()
</script>

<template>
    <div class="pt-6">
        <ul class="flex flex-col gap-5 items-center">
            <li v-for="{ name, age, id } in users" :key="id" class="flex gap-4 text-lg border-cyan-800 border-2 p-4">
                {{ name }} is {{ age }} years old
                <button @click="deleteUser(id)">
                    <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6 text-red-600" fill="none" viewBox="0 0 24 24"
                        stroke="currentColor">
                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
                    </svg>
                </button>
            </li>
        </ul>
    </div>
</template>