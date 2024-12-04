<script setup>
import { inject } from 'vue';

defineProps({
  id: Number,
  imageUrl: String,
  title: String,
  price: Number,
  isFavorite: Boolean,
  isAdded: Boolean,
});

const addToFavorite = inject('addToFavorite');
const addToCart = inject('addToCart');
</script>

<template>
  <article
    class="bg-white rounded-3xl p-6 md:p-8 relative border-slate-100 cursor-pointer hover:-translate-y-2 hover:shadow-xl transition duration-300"
  >
    <img
      class="absolute cursor-pointer"
      :src="isFavorite ? '/like-2.svg' : '/like-1.svg'"
      alt="Like"
      @click="() => addToFavorite(id)"
    />
    <img class="mb-3 md:h-56 m-auto" :src="imageUrl" alt="Sneakers" />
    <p class="mb-5 md:min-h-12">{{ title }}</p>

    <div class="flex justify-between items-center">
      <div class="flex flex-col">
        <span class="text-gray-400">Ціна:</span>
        <b>{{ price }} ₴</b>
      </div>

      <img
        class="cursor-pointer"
        :src="isAdded ? '/checked.svg' : '/plus.svg'"
        alt="Add"
        @click="() => addToCart(id)"
      />
    </div>
  </article>
</template>
