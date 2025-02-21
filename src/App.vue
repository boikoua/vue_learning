<script setup>
import { ref } from 'vue';

const value = ref('');
const text = ref('');

function showText() {
  text.value = value.value;
}

const mouseValue = ref('middle');
</script>

<template>
  <input type="text" v-model="value" @keyup.enter="showText" />

  <p>{{ text }}</p>

  <hr />

  <a href="#" @click.prevent="mouseValue = 'left'" @contextmenu.prevent="mouseValue = 'right'"
    >LINK</a
  >

  <p>{{ mouseValue }}</p>
</template>

<style scoped></style>
