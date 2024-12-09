<script setup>
import { computed, onMounted, provide, reactive, ref, watch } from 'vue';
import axios from 'axios';

import Home from './pages/Home.vue';
import Header from './components/Header.vue';
import Drawer from './components/Drawer.vue';
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

    // Достаем данные из localStorage
    const storedItems = JSON.parse(localStorage.getItem('items')) || [];

    // Сравниваем и обновляем свойства
    items.value = data.map((item) => {
      const storedItem = storedItems.find((stored) => stored.id === item.id);

      return {
        ...item,
        isFavorite: storedItem ? storedItem.isFavorite : false,
        isAdded: storedItem ? storedItem.isAdded : false,
      };
    });

    localStorage.setItem('items', JSON.stringify(items.value));
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

  localStorage.setItem('items', JSON.stringify(items.value));
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

  localStorage.setItem('items', JSON.stringify(items.value));
};

// Подсчет общей суммы товаров в корзине
const totalSum = computed(() =>
  items.value.filter((item) => item.isAdded).reduce((acc, item) => acc + item.price, 0),
);

const taxSum = computed(() => Math.round(totalSum.value * 0.25));

// Функция для отправки заказа
const sendOrder = () => {
  items.value = items.value.map((item) => {
    return {
      ...item,
      isAdded: false,
    };
  });

  localStorage.setItem('items', JSON.stringify(items.value));
};

// Хук, для запроса данных при монтировании компоненты
onMounted(async () => {
  const isKey = localStorage.getItem('items');

  if (!isKey) {
    await fetchItems();
  } else {
    items.value = JSON.parse(localStorage.getItem('items'));
  }
});

// Функция, которая следит за изменением переменной filters
watch(filters, fetchItems);

// Альтернатива контекста
provide('addToFavorite', addToFavorite);
provide('addToCart', addToCart);
provide('isCloseDraw', closeOrOpenDrawer);
provide('items', items);
provide('totalSum', totalSum);
provide('taxSum', taxSum);
</script>

<template>
  <Drawer v-if="drawerOpen" :items="items" :sendOrder="sendOrder" />

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
      <Home
        :filters="filters"
        :onChangeSelect="onChangeSelect"
        :onChangeSearch="onChangeSearch"
        :clearSearch="clearSearch"
      />
    </main>
  </div>
</template>

<style scoped></style>
