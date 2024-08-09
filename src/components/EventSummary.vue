<script setup lang="ts">
import {ref} from 'vue'
import type { Event } from '@/types';
defineProps<{
    event: Event
}>()
</script>

<template>
    <div class="event-summary">
          <div class="cursor-pointer border border-gray-600 p-[20px] w-[250px] mb-[18px] justify-end text-right hover:scale-101 hover:shadow-sp">
            <span class="ml-2">{{ event.category }}</span>
            <span class="ml-2">{{ event.organizer }}</span>
    </div>
</div>
  </template>

  