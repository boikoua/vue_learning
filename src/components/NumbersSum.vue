<script setup>
const props = defineProps({
  nums: Array,
});

const sum = props.nums.reduce((acc, num) => acc + num, 0);
</script>

<template>
  <p>Sum = {{ sum }}</p>
</template>
