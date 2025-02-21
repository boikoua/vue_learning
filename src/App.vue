<script setup>
import NumberSquared from './components/NumberSquared.vue';
import NumbersSum from './components/NumbersSum.vue';

const linkObj = {
  logo: 'logo.png',
  link: 'https://google.com',
  alt: 'Google logo',
};

const numsForSum = [1, 2, 3, 4, 5];
</script>

<template>
  <a :href="linkObj.link" target="_blank">
    <img :src="linkObj.logo" :alt="linkObj.alt" />
  </a>
  <h2>Number squared</h2>
  <NumberSquared :num="5" />
  <h2>Numbers sum</h2>
  <NumbersSum :nums="numsForSum" />
</template>

<style scoped>
img {
  width: 150px;
  height: 150px;
  transition: all 0.3s;
}

img:hover {
  transform: scale(1.05);
}
</style>
