<script setup lang="ts">
import { ref } from 'vue'
import UserList from '@/components/UserList.vue';
import Form from '@/components/Form-Create.vue';
import Button from '@/components/Custom-Button.vue'
import type { User } from '@/types/User';

const count = ref(0)

const users = ref<User[]>([
  { name: 'John Doe', age: 30, id: 1 },
  { name: 'Jane Doe', age: 25, id: 2 },
  { name: 'John Smith', age: 35, id: 3 },
])

const incrementCount = () => {
  count.value++
}

export type createUserProps = Omit<User, 'id'>
const createUser = ({ name, age }: createUserProps) => {
  if (name && age) {
    users.value.push({
      name,
      age,
      id: Math.random() * 100,
    })
  }
}

const deleteUser = (id: number) => {
  users.value = users.value.filter((user) => user.id !== id)
}
</script>

<template>
  <section class="py-6">
    <h1 class="text-2xl text-red-600 text-center">
      Welcome to Vue 3 + Vite + TypeScript + Tailwind CSS
    </h1>
    <div class="flex flex-col gap-5 items-center">
      <span>
        {{ count }}
      </span>
      <Button @click="incrementCount" :color="'success'">count is: </Button>
    </div>
    <div>
      <h2 class="text-2xl text-red-600 text-center">
        Users
      </h2>
      <Form :createUser="createUser" />
    </div>
    <UserList :users="users" :deleteUser="deleteUser" />
  </section>
</template>