<script setup>
const user = 'John';

function greeting() {
  console.log(`Hello ${user}`);
}

const clickFunc = () => {
  console.log('Click event!');
};

const blurFunc = () => {
  console.log('Blur event!');
};

function getDayOfWeek(num) {
  return new Date(2025, 1, num).getDay();
}

function showDay(num) {
  return getDayOfWeek(num);
}
</script>

<template>
  <button @click="clickFunc" @mouseenter="blurFunc">Click show</button>
  <br />
  <br />
  <button @click="greeting">Click greeting</button>

  <p>{{ showDay(21) }}</p>
</template>

<style scoped></style>
