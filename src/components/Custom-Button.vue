<script setup lang="ts">
type ButtonProps = {
    size?: 'small' | 'medium' | 'large' | 'base'
    color?: 'primary' | 'secondary' | 'success' | 'danger' | 'warning' | 'info'
    disabled?: boolean
    type?: 'button' | 'submit' | 'reset'
}

withDefaults(
    defineProps<ButtonProps>(),
    {
        disabled: false,
        size: 'base',
        color: 'primary',
        type: 'button',
    }
)
</script>


<template>
    <button :type="type" :disabled="disabled" class="rounded-lg" :class="{
        'px-2 py-1': size === 'small',
        'px-8 py-4': size === 'base',
        'px-4 py-2': size === 'medium',
        'px-6 py-3': size === 'large',
        'bg-blue-500 hover:bg-blue-700 text-white font-bold': color === 'primary',
        'bg-green-500 hover:bg-green-700 text-white font-bold': color === 'success',
        'bg-red-500 hover:bg-red-700 text-white font-bold': color === 'danger',
        'bg-yellow-500 hover:bg-yellow-700 text-white font-bold': color === 'warning',
        'bg-gray-500 hover:bg-gray-700 text-white font-bold': color === 'secondary',
        'bg-indigo-500 hover:bg-indigo-700 text-white font-bold': color === 'info',

    }">
        <slot />
    </button>
</template>

