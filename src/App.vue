<script setup>
import Header from './components/Header.vue';
import CardList from './components/CardList.vue';
import Drawer from './components/Drawer.vue';

const items = [
  {
    id: 1,
    title: 'Чоловічі Кросівки Nike Blazer Mid Suede',
    price: 12999,
    imageUrl: '/sneakers/sneakers-1.jpg',
  },
  {
    id: 2,
    title: 'Чоловічі Кросівки Nike Air Max 270',
    price: 15600,
    imageUrl: '/sneakers/sneakers-2.jpg',
  },
  {
    id: 3,
    title: 'Чоловічі Кросівки Nike Blazer Mid Suede',
    price: 8499,
    imageUrl: '/sneakers/sneakers-3.jpg',
  },
  {
    id: 4,
    title: 'Кросівки Puma X Aka Boku Future Rider',
    price: 7800,
    imageUrl: '/sneakers/sneakers-4.jpg',
  },
  {
    id: 5,
    title: 'Кросівки Future Rider',
    price: 9550,
    imageUrl: '/sneakers/sneakers-5.jpg',
  },
  {
    id: 6,
    title: 'Кросівки Black Edition',
    price: 16999,
    imageUrl: '/sneakers/sneakers-6.jpg',
  },
  {
    id: 7,
    title: 'Кросівки Orange Boomb Edition',
    price: 7499,
    imageUrl: '/sneakers/sneakers-7.jpg',
  },
  {
    id: 8,
    title: 'Кросівки Nike Air Max 270',
    price: 15600,
    imageUrl: '/sneakers/sneakers-8.jpg',
  },
  {
    id: 9,
    title: 'Кросівки Nike Air Force 1',
    price: 5900,
    imageUrl: '/sneakers/sneakers-9.jpg',
  },
  {
    id: 10,
    title: 'Кросівки Adidas Ultraboost',
    price: 11500,
    imageUrl: '/sneakers/sneakers-10.jpg',
  },
  {
    id: 11,
    title: 'Кросівки Puma Clyde All-Pro',
    price: 7600,
    imageUrl: '/sneakers/sneakers-11.jpg',
  },
  {
    id: 12,
    title: 'Кросівки Converse Chuck Taylor All-Star',
    price: 13000,
    imageUrl: '/sneakers/sneakers-12.jpg',
  },
];
</script>

<template>
  <!-- <Drawer /> -->
  <div class="w-4/5 m-auto bg-white rounded-xl shadow-xl my-10">
    <Header />

    <main class="p-10">
      <div class="flex justify-between items-center">
        <h2 class="text-3xl font-bold mb-8">Усі кросівки</h2>

        <div class="flex gap-4">
          <select class="py-1.5 px-3 border rounded-md outline-none">
            <option value="">За назвою</option>
            <option value="">За ціною (від меншої)</option>
            <option value="">За ціною (від більшої)</option>
          </select>

          <div class="relative">
            <img class="absolute top-2 left-3" src="/search.svg" alt="Search" />
            <input
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
