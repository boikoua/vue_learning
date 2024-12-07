<script setup>
defineProps({
  imageUlr: String,
  title: String,
  description: String,
});
</script>

<template>
  <div class="flex flex-col gap-1 items-center m-auto text-center max-w-56">
    <img class="w-16 mb-4" :src="imageUlr" alt="Info image" />
    <h2 class="text-2xl font-medium">{{ title }}</h2>
    <p class="text-gray-400">{{ description }}</p>
  </div>
</template>
