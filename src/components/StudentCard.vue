<script setup lang="ts">
// import { ref } from 'vue'
import type { Student } from '@/types';
defineProps<{
    student: Student
}>()
</script>

<template>
    <div class="student-class">
        <div class="cursor-pointer border border-gray-600 p-5 w-64 mb-4 hover:scale-105 hover:shadow-lg transition-transform">
            <h2>{{ student.name }} {{ student.surname }}</h2>
            <p>{{ student.gpa }}</p>
        </div>
    </div>
</template>
