<script setup>
import CardList from '@/components/CardList.vue';
import { inject } from 'vue';

defineProps({
  filters: Object,
  onChangeSelect: Function,
  onChangeSearch: Function,
  clearSearch: Function,
});

const items = inject('items');
</script>

<template>
  <div class="flex flex-col md:flex-row md:justify-between md:items-center gap-4 mb-5 md:mb-10">
    <h2 class="text-2xl md:text-4xl font-bold">Усі кросівки</h2>

    <div class="flex flex-col md:flex-row gap-4">
      <select
        class="w-full md:w-32 py-2 px-3 border border-gray-200 rounded-md"
        @change="onChangeSelect"
        :value="filters.sortBy"
      >
        <option value="-title">По назві (⭡)</option>
        <option value="title">По назві (⭣)</option>
        <option value="-price">По ціні (⭡)</option>
        <option value="price">По ціні (⭣)</option>
      </select>

      <div class="relative">
        <img class="absolute top-3 left-2" src="/search.svg" alt="Search" />
        <input
          class="border w-full md:w-56 lg:w-80 border-gray-200 rounded-md py-2 px-8 outline-none focus:border-gray-400"
          type="text"
          placeholder="Пошук..."
          :value="filters.searchValue"
          @input="onChangeSearch"
        />
        <img
          v-if="filters.searchValue"
          class="absolute w-5 top-3 right-2 cursor-pointer"
          src="/clear.svg"
          alt="Clear"
          @click="clearSearch"
        />
      </div>
    </div>
  </div>

  <CardList :items="items" />
</template>
