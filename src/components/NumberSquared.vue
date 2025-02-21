<script setup>
defineProps({
  num: Number,
});
</script>

<template>
  <p>Squared from {{ num }} will be {{ Math.pow(num, 2) }}</p>
</template>
