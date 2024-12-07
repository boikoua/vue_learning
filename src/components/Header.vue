<script setup>
defineProps({
  isOpenDraw: Function,
  isOpenBurger: Function,
});
</script>

<template>
  <header
    class="flex justify-between items-center border-b border-slate-300 px-3 md:px-10 py-4 md:py-6"
  >
    <div class="flex items-center gap-2 md:gap-4">
      <img class="h-8 md:h-10" src="/logo.png" alt="Logo" />
      <div>
        <h2 class="text-base md:text-2xl font-bold uppercase">Sneakers</h2>
        <p class="text-xs md:text-sm text-slate-400">Магазин найкращих кросівок</p>
      </div>
    </div>

    <ul class="hidden md:flex items-center gap-5">
      <li
        class="flex items-center gap-2 text-gray-400 hover:text-gray-600 cursor-pointer transition duration-300"
        @click="isOpenDraw"
      >
        <img src="/cart.svg" alt="Cart" />
        <span>1205 ₴</span>
      </li>

      <li
        class="flex items-center gap-2 text-gray-400 hover:text-gray-600 cursor-pointer transition duration-300"
      >
        <img src="/heart.svg" alt="Cart" />
        <span>Збереження</span>
      </li>

      <li
        class="flex items-center gap-2 text-gray-400 hover:text-gray-600 cursor-pointer transition duration-300"
      >
        <img src="/profile.svg" alt="Cart" />
        <span>Профіль</span>
      </li>
    </ul>

    <img
      class="block md:hidden w-7 cursor-pointer"
      src="/burger.svg"
      alt="Menu"
      @click="isOpenBurger"
    />
  </header>
</template>
