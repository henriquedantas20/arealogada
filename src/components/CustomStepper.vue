<template>
    <div class="stepper-wrapper">
        <div class="stepper-progress"></div>
    </div>
</template>

<script lang="ts" setup>
import { computed } from 'vue';

    const props = defineProps<{
        current: number,
        total: number,
    }>()

    const currentProgress = computed(() => `${(100 / props.total) * props.current}%`)
</script>

<style>
    .stepper-wrapper {
        width: 100%;
        height: 6px;
        border-radius: 10px;
        background-color: #EDEDED;
        display: flex;
        justify-content: flex-start;
    }

    .stepper-progress {
        width: v-bind(currentProgress);
        height: 100%;
        background-color: #FC4D04;
        border-radius: 10px;
        transition: all .2s;
    }
</style>