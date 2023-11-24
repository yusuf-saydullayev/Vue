<script setup lang="ts">
import type { createUserProps } from '@/pages/Home-Page.vue';
import { ref } from 'vue';
import Button from '@/components/Custom-Button.vue'

type ComponentProps = {
    createUser: ({ name, age }: createUserProps) => void,
}
const { createUser } = defineProps<ComponentProps>();

const userName = ref<string>('')
const userAge = ref<number>(0)

const onSubmit = () => {
    if (userName.value && userAge.value) {
        createUser({ name: userName.value, age: userAge.value })
        userName.value = ''
        userAge.value = 0
    }
}

</script>

<template>
    <div class="flex gap-14 justify-center">
        <form @submit.prevent="onSubmit" class="flex flex-col gap-5 p-4 border-2 border-fuchsia-700">
            <input v-model.trim="userName" type="text" placeholder="Name"
                class="px-3 py-2 bg-white border border-slate-300 rounded-md shadow-sm placeholder-slate-400" />
            <input v-model.number="userAge" type="number" placeholder="Age" min="1"
                class="px-3 py-2 bg-white border border-slate-300 rounded-md shadow-sm placeholder-slate-400" />
            <Button type="submit">
                Add User
            </Button>
        </form>
    </div>
</template>