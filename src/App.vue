<script setup>
import { onMounted, reactive, ref, watch } from 'vue';
import axios from 'axios';

import Header from './components/Header.vue';
import CardList from './components/CardList.vue';
import Drawer from './components/Drawer.vue';

const items = ref([]);

const filters = reactive({
  sortBy: '',
  searchQuery: '',
});

const onChangeSelect = event => {
  filters.sortBy = event.target.value;
};

const onChangeSearch = event => {
  filters.searchQuery = event.target.value;
};

onMounted(async () => {
  try {
    const { data } = await axios.get(
      'https://1e2507bc8b8d8220.mokky.dev/items',
    );

    items.value = data;
  } catch (error) {
    console.log(error);
  }
});

watch(filters, async () => {
  try {
    const { data } = await axios.get(
      `https://1e2507bc8b8d8220.mokky.dev/items?sortBy=${filters.sortBy}&title=*${filters.searchQuery}*`,
    );

    items.value = data;
  } catch (error) {
    console.log(error);
  }
});
</script>

<template>
  <!-- <Drawer /> -->
  <div class="w-4/5 m-auto bg-white rounded-xl shadow-xl my-10">
    <Header />

    <main class="p-10">
      <div class="flex justify-between items-center mb-10">
        <h2 class="text-3xl font-bold mb-8">Усі кросівки</h2>

        <div class="flex gap-4">
          <select
            @change="onChangeSelect"
            class="py-1.5 px-3 border rounded-md outline-none"
          >
            <option value="title">За назвою</option>
            <option value="price">За ціною (від меншої)</option>
            <option value="-price">За ціною (від більшої)</option>
          </select>

          <div class="relative">
            <img class="absolute top-2 left-3" src="/search.svg" alt="Search" />
            <input
              @change="onChangeSearch"
              class="border rounded-md py-1 pl-10 pr-4 outline-none focus:border-gray-400"
              type="text"
              placeholder="Пошук..."
            />
          </div>
        </div>
      </div>

      <CardList :items="items" />
    </main>
  </div>
</template>

<style scoped></style>
