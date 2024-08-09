<script setup lang="ts">
import { ref, watch } from 'vue';
import { useRouter, useRoute } from 'vue-router';
import { useMessageStore } from './stores/message';
import { storeToRefs } from 'pinia';
const store = useMessageStore()
const {message} = storeToRefs(store)

const router = useRouter();
const route = useRoute();

const pageSize = ref(parseInt(route.query.pageSize as string) || 10);

const updatePageSize = () => {
  router.push({ name: 'event-list-view', query: { ...route.query, pageSize: pageSize.value, page: 1 } });
};

watch(
  () => route.query.pageSize,
  (newVal) => {
    pageSize.value = parseInt(newVal as string) || 10;
  }
);
</script>

<template>
  <SpeedInsight/>
    <div class="text-center font-sans text-gray-700 antialias">
    <header>
      <div id="flashMessage" class="animate-fade" v-if="message">
      <h4>{{ message }}</h4>
      </div>
      <h1 class="text-4xl mb-8" >Deploy with Vercel</h1>
      <div class="wrapper">
        <nav class="py-6">
          <RouterLink class="font-bold text-gray-700" exact-active-class="text-green-500" :to="{ name: 'event-list-view' }">Event</RouterLink> |
          <RouterLink class="font-bold text-gray-700" exact-active-class="text-green-500" :to="{ name: 'student' }">Student</RouterLink> |
          <RouterLink class="font-bold text-gray-700" exact-active-class="text-green-500" :to="{ name: 'about' }">About</RouterLink>
        </nav>
        <div class="pagination-controls mt-5">
          <label for="pageSize" class="mr-2">Events per page:</label>
          <select id="pageSize" v-model="pageSize" @change="updatePageSize" class="border border-gray-300 rounded px-2 py-1">
            <option value="2">2</option>
            <option value="4">4</option>
            <option value="6">6</option>
            <option value="8">8</option>
          </select>
        </div>
      </div>
    </header>
    <RouterView />
  </div>
</template>


