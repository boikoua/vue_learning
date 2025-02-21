<script setup>
import { ref } from 'vue';

const visible = ref(true);

const isShow = ref(true);

const day = 4;

const days = ['Sunday', 'Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday', 'Saturday'];
</script>

<template>
  <!-- v-if, v-else, v-else-if -->
  <button @click="() => (visible = !visible)">{{ visible ? 'Hide' : 'Show' }}</button>

  <div v-if="visible">
    Lorem ipsum dolor sit, amet consectetur adipisicing elit. Eligendi, ipsa praesentium ex vel odit
    perferendis distinctio excepturi rerum delectus nihil?
  </div>
  <div v-else>This content is hidden</div>

  <div class="days">
    <p v-if="day === 0">{{ days[0] }}</p>
    <p v-if="day === 1">{{ days[1] }}</p>
    <p v-if="day === 2">{{ days[2] }}</p>
    <p v-if="day === 3">{{ days[3] }}</p>
    <p v-if="day === 4">{{ days[4] }}</p>
    <p v-if="day === 5">{{ days[5] }}</p>
    <p v-if="day === 6">{{ days[6] }}</p>
  </div>

  <!-- v-show -->
  <button @click="() => (isShow = !isShow)">{{ isShow ? 'hide' : 'show' }}</button>
  <p v-show="isShow">Lorem ipsum dolor sit amet.</p>
</template>

<style scoped>
.days {
  border: 1px solid gray;
}
</style>
