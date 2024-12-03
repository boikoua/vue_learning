<script setup>
import Header from './components/Header.vue';
import CardList from './components/CardList.vue';
import Drawer from './components/Drawer.vue';
</script>

<template>
  <!-- <Drawer /> -->

  <div class="w-11/12 lg:w-4/5 m-auto bg-zinc-100 rounded-2xl shadow-xl my-4 md:my-6 lg:my-10">
    <Header />

    <main class="p-4 md:p-10">
      <div class="flex flex-col md:flex-row md:justify-between md:items-center gap-4 mb-5 md:mb-10">
        <h2 class="text-2xl md:text-4xl font-bold">Усі кросівки</h2>

        <div class="flex flex-col md:flex-row gap-4">
          <select class="w-full md:w-30 py-2 px-3 border border-gray-200 rounded-md">
            <option value="">По назві (⭡)</option>
            <option value="">По назві (⭣)</option>
            <option value="">По ціні (⭣)</option>
            <option value="">По ціні (⭡)</option>
          </select>

          <div class="relative">
            <img class="absolute top-3 left-2" src="/search.svg" alt="Search" />
            <input
              class="border w-full md:w-56 lg:w-80 border-gray-200 rounded-md py-2 pl-8 pr-2 outline-none focus:border-gray-400"
              type="text"
              placeholder="Пошук..."
            />
          </div>
        </div>
      </div>

      <CardList />
    </main>
  </div>
</template>

<style scoped></style>
