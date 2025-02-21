<script setup>
import { ref } from 'vue';

const cssClasses = 'color bg-color border padding';

const cssObject = ref({
  done: true,
  selected: false,
});

const isValid = true;
const isDisabled = true;
</script>

<template>
  <p :class="cssClasses">
    Lorem ipsum dolor sit amet consectetur adipisicing elit. Reprehenderit consequuntur enim quo
    reiciendis nam obcaecati vero, facilis recusandae soluta nesciunt?
  </p>

  <p :class="cssObject">
    Lorem ipsum dolor sit amet, consectetur adipisicing elit. Ullam cum ut ratione saepe
    perferendis. Ratione enim optio nihil natus minus numquam animi, distinctio dignissimos neque,
    sunt ipsa? Eaque, officiis earum.
  </p>

  <button
    @click="
      () => {
        cssObject.done = !cssObject.done;
        cssObject.selected = !cssObject.selected;
      }
    "
  >
    toggle
  </button>

  <p :class="{ 'bg-color': isValid, padding: isDisabled }">
    Lorem ipsum, dolor sit amet consectetur adipisicing elit. Illum numquam incidunt aut!
  </p>

  <p
    :style="{
      color: 'green',
      'background-color': 'yellow',
      fontWeight: 'bold',
      'font-style': 'italic',
    }"
  >
    Lorem ipsum dolor, sit amet consectetur adipisicing elit. Officia, numquam quis rerum et, nihil
    natus beatae quia facilis incidunt dolore aut pariatur animi ex! Qui harum temporibus totam
    laborum non sequi pariatur? Illo a accusamus assumenda quaerat iusto amet minus. Debitis
    consequuntur delectus quis a dolore, excepturi numquam quos quas?
  </p>
</template>

<style scoped>
.color {
  color: blue;
}

.bg-color {
  background-color: orangered;
}

.border {
  border: 2px solid gray;
}

.padding {
  padding: 10px 20px;
}

.done {
  background-color: greenyellow;
  text-decoration: line-through;
  transition: all 1s;
}

.selected {
  background-color: bisque;
  transition: all 1s;
}
</style>
