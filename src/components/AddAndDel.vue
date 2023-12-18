<script setup>
import { ref } from 'vue'

const number = ref(0)
</script>
<template>
    <div>
        <p>ref测试</p>
        <p>{{ number }}</p>
        <button @click="number++">+1</button>
        <button @click="number--">-1</button>
    </div>
</template>
<style></style> 