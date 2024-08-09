<script setup lang="ts">
import StudentCard from '@/components/StudentCard.vue';
import type { Student } from '@/types';
import { ref, onMounted } from 'vue';
import StudentService from '@/services/StudentService';

const students = ref<Student[]>([]);

onMounted(() => {
  StudentService.getEvents()
    .then((response) => {
      students.value = response.data;
    })
    .catch((error) => {
      console.error('There was an error', error);
    });
});
</script>

<template>
  <h1 class="text-2xl font-bold mb-4">Student</h1>
  <div class="flex flex-col items-center">
    <StudentCard v-for="student in students" :key="student.id" :student="student" />
  </div>
</template>

