<script setup>
import { inject } from 'vue';

const isCloseDraw = inject('isCloseDraw');
</script>

<template>
  <div class="flex gap-4 items-center mb-5">
    <img
      class="rotate-180 transition hover:opacity-70 cursor-pointer"
      src="/arrow-right.svg"
      alt="Back"
      @click="isCloseDraw"
    />
    <h2 class="text-2xl font-bold">Кошик</h2>
  </div>
</template>
