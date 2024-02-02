<template>
    <label class="input-wrapper">
        <input :placeholder="label" type="text" :name="name" :value="value" @input="handleChange" />
        <p v-if="error">{{ error }}</p>
    </label>
</template>

<script lang="ts" setup>
    defineProps<{
        label: string,
        name: string,
        value: string,
        error?: string
    }>()

    const emit = defineEmits(['change'])

    const handleChange = (event: Event) => {
        emit('change', (event?.target as HTMLInputElement)?.value)
    }
</script>

<style>
    .input-wrapper {
        display: flex;
        justify-content: flex-start;
        height: 65px;
        padding: 15px 20px;
        width: 100%;
        border: 1.5px solid #D5D5D5;
        border-radius: 20px;
    }

    input {
        width: 100%;
        border: none;
        outline: none;
        font-size: 16px;
        line-height: 17.6px;
        font-weight: 400;
    }

    input::placeholder {
        color: black;
        font-family: 'IBM Plex Sans';
    }

    @media (min-width: 1024px) {
        
    }
</style>