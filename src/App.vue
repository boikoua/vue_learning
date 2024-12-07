<script setup>
import { computed, onMounted, provide, reactive, ref, watch } from 'vue';

import Header from './components/Header.vue';
import CardList from './components/CardList.vue';
import Drawer from './components/Drawer.vue';
import axios from 'axios';
import BurgerMenu from './components/BurgerMenu.vue';

const DATA_LINK = 'https://1e2507bc8b8d8220.mokky.dev/items';

const items = ref([]);
const isError = ref('');
const isLoading = ref(true);

// Флаг для открытия корзины
const drawerOpen = ref(false);

// Функция для закрытия/открытия корзины
const closeOrOpenDrawer = () => {
  drawerOpen.value = !drawerOpen.value;
};

// Флаг для открытия бургер меню
const burgerOpen = ref(false);

// Функция для закрытия/открытия бургер меню
const closeOrOpenBurger = () => {
  burgerOpen.value = !burgerOpen.value;
};

// Реактив для хранения значений фильтрации
// (применять для работы с объектами)

const filters = reactive({
  sortBy: 'price',
  searchValue: '',
});

// Хендл для обработки селекта
const onChangeSelect = (event) => {
  filters.sortBy = event.target.value;
};

// Хендл для обработки инпута
const onChangeSearch = (event) => {
  filters.searchValue = event.target.value;
};

// Функция очистки поиска
const clearSearch = () => {
  filters.searchValue = '';
};

// Функция для запроса данных
const fetchItems = async () => {
  try {
    // Объект параметров для фильтрации
    const params = {
      sortBy: filters.sortBy,
    };

    // Проверяю наличие значения в поиске
    if (filters.searchValue) {
      params.title = `*${filters.searchValue}*`;
    }

    const { data } = await axios.get(DATA_LINK, { params });

    items.value = data.map((item) => {
      return {
        ...item,
        isFavorite: false,
        isAdded: false,
      };
    });
  } catch {
    isError.value = 'Виникла помилка, перезавантажте сторінку...';
  } finally {
    isLoading.value = false;
  }
};

const addToFavorite = (id) => {
  items.value = items.value.map((item) => {
    if (item.id === id) {
      return {
        ...item,
        isFavorite: !item.isFavorite,
      };
    }

    return item;
  });
};

const addToCart = (id) => {
  items.value = items.value.map((item) => {
    if (item.id === id) {
      return {
        ...item,
        isAdded: !item.isAdded,
      };
    }

    return item;
  });
};

// Подсчет общей суммы товаров в корзине
const totalSum = computed(() =>
  items.value.filter((item) => item.isAdded).reduce((acc, item) => acc + item.price, 0),
);

// Хук, для запроса данных при монтировании компоненты
onMounted(fetchItems);

// Функция, которая следит за изменением переменной filters
watch(filters, fetchItems);

// Альтернатива контекста
provide('addToFavorite', addToFavorite);
provide('addToCart', addToCart);
provide('isCloseDraw', closeOrOpenDrawer);
provide('items', items);
provide('totalSum', totalSum);
</script>

<template>
  <Drawer v-if="drawerOpen" :items="items" />
  <BurgerMenu
    v-if="burgerOpen"
    :isCloseBurger="closeOrOpenBurger"
    :isOpenDrawer="closeOrOpenDrawer"
  />

  <div
    class="w-11/12 lg:w-4/5 m-auto bg-zinc-100 rounded-2xl shadow-xl my-4 md:my-6 lg:my-10 min-h-screen"
  >
    <Header
      :totalSum="totalSum"
      :isOpenDrawer="closeOrOpenDrawer"
      :isOpenBurger="closeOrOpenBurger"
    />

    <main class="p-4 md:p-10">
      <div class="flex flex-col md:flex-row md:justify-between md:items-center gap-4 mb-5 md:mb-10">
        <h2 class="text-2xl md:text-4xl font-bold">Усі кросівки</h2>

        <div class="flex flex-col md:flex-row gap-4">
          <select
            class="w-full md:w-32 py-2 px-3 border border-gray-200 rounded-md"
            @change="onChangeSelect"
            v-model="filters.sortBy"
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
    </main>
  </div>
</template>

<style scoped></style>
