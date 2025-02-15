<script setup>
import { computed, onUnmounted, reactive, ref, watch } from 'vue';

// const count = ref(0);

const state = reactive({
  count: 0,
  title: 'Count value is',
});

let timer = null;

const startTimer = () => {
  if (!timer) {
    timer = setInterval(() => {
      state.count++;
    }, 1000);
  }
};

const stopTimer = () => {
  if (timer) {
    clearInterval(timer);
    timer = null;
  }
};

onUnmounted(() => {
  clearInterval(timer);
});

const increment = () => {
  state.count++;
  stopTimer();
};

const decrement = () => {
  if (state.count > 0) {
    state.count--;
  }
  stopTimer();
};

const reset = () => {
  state.count = 0;
  stopTimer();
};

const dynamicTitle = computed(() => {
  return state.count > 10 ? '🔥 High count!' : 'Count value is';
});

watch(
  () => state.count,
  () => {
    console.log(state.count);
  }
);
</script>

<template>
  <div>
    <h2>
      {{ dynamicTitle }}:
      <span
        :style="{
          color:
            state.count === 0 ? 'green' : state.count > 5 ? 'purple' : 'orange',
        }"
        >{{ state.count }}</span
      >
    </h2>

    <div class="btns">
      <button @click="increment">+</button>
      <button @click="reset">Reset</button>
      <button @click="decrement">-</button>
      <button @click="startTimer">Start timer</button>
      <button @click="stopTimer">Stop timer</button>
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
