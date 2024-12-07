<script setup>
const props = defineProps({
  isOpenDraw: Function,
  isCloseBurger: Function,
});

const isCloseBurgerAndOpenCart = () => {
  props.isCloseBurger();
  setTimeout(() => {
    props.isOpenDraw();
  }, 100); // Укажите задержку, если нужно
};
</script>

<template>
  <img
    src="/close-burger.svg"
    alt="Close"
    class="absolute z-50 w-7 cursor-pointer right-6 top-9"
    @click="isCloseBurger"
  />
  <ul
    class="flex flex-col h-screen justify-center bg-zinc-100 items-center gap-5 absolute inset-0 z-40"
  >
    <li
      class="flex items-center gap-2 text-xl text-gray-400 hover:text-gray-600 cursor-pointer transition duration-300"
      @click="isCloseBurgerAndOpenCart"
    >
      <img src="/cart.svg" alt="Cart" />
      <span>Корзина (1205 ₴)</span>
    </li>

    <li
      class="flex items-center gap-2 text-xl text-gray-400 hover:text-gray-600 cursor-pointer transition duration-300"
    >
      <img src="/heart.svg" alt="Cart" />
      <span>Збереження</span>
    </li>

    <li
      class="flex items-center gap-2 text-xl text-gray-400 hover:text-gray-600 cursor-pointer transition duration-300"
    >
      <img src="/profile.svg" alt="Cart" />
      <span>Профіль</span>
    </li>
  </ul>
</template>
