<script setup>
import Header from './components/Header.vue';
import CardList from './components/CardList.vue';
</script>

<template>
  <div class="w-11/12 lg:w-4/5 m-auto bg-zinc-100 rounded-2xl shadow-xl my-4 md:my-6 lg:my-10">
    <Header />

    <main class="p-4 md:p-10">
      <h2 class="text-2xl md:text-4xl font-bold mb-4 md:mb-10">Усі кросівки</h2>

      <CardList />
    </main>
  </div>
</template>

<style scoped></style>
