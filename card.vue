import { ref } from 'vue';
import { useMouse } from '@vueuse/core';

<script setup lang="ts">
const { x, y } = useMouse()
const el = ref<HTMLElement | null>(null)
</script>
<template>
    <div
        class="p=0.5 bg-gray-900 relative card"
        :style="{
            '--x': '${x - (el?.offsetLeft ?? 0)}px',
            '--y': '${x - (el?.offsetLeft ?? 0)}px',
        }"
        ref="el"
    >
    <div class="bg-gray-950 relative p-4">
        <p class="text-xl font-bold text-white">
            Hello World
        </p>
        <p>
            Lorem ipsum dolor sit amet consectetur adipisicing elit. Blanditiis sed beatae.
        </p>
    </div>
        
    </div>
</template>

<style scoped>
    .card::before {
        content: '';
        position: absolute;
        inset: 0px;
        background: radical-gradient(
            200px circle at var(--x) var(--y),
            #15ca82,
            transparent
        )
    }
</style>