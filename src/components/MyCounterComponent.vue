<script setup>
import { reactive, ref } from 'vue';

// const count = ref(0);

const state = reactive({
  count: 0,
  title: 'Count value is',
});

const increment = () => {
  state.count++;
};

const decrement = () => {
  if (state.count > 0) {
    state.count--;
  }
};
</script>

<template>
  <div>
    <h2>
      {{ state.title }}: <span>{{ state.count }}</span>
    </h2>

    <div class="btns">
      <button @click="increment">+</button>
      <button @click="decrement">-</button>
    </div>
  </div>
</template>

<style scoped>
span {
  color: purple;
  font-size: 26px;
}

.btns {
  display: flex;
  gap: 20px;
}

button {
  padding: 10px 20px;
  font-size: 18px;
  border: none;
  background-color: #6200ea;
  color: white;
  cursor: pointer;
  transition: background 0.3s;
}

button:hover {
  background-color: #3700b3;
}
</style>
