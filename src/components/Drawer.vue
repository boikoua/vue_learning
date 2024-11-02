<script setup>
import DrawerHead from './DrawerHead.vue';
import CartItemList from './CartItemList.vue';
</script>

<template>
  <div class="fixed top-0 left-0 h-full w-full bg-black z-10 opacity-70"></div>
  <div class="fixed top-0 right-0 bg-white w-96 h-full z-20 p-8">
    <DrawerHead />

    <CartItemList />

    <div class="flex flex-col gap-6 my-8">
      <div class="flex justify-between gap-3">
        <span>Всього:</span>
        <div class="border-b border-dotted flex-1"></div>
        <b>12999 ₴</b>
      </div>

      <div class="flex justify-between gap-3">
        <span>НДС 5%::</span>
        <div class="border-b border-dotted flex-1"></div>
        <b>999 ₴</b>
      </div>

      <button
        :disabled="false"
        class="bg-lime-500 w-full rounded-2xl py-3 text-white transition cursor-pointer disabled:bg-slate-400 hover:bg-lime-600 active:bg-lime-700"
      >
        Зробити замовлення
      </button>
    </div>
  </div>
</template>
