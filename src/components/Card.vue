<script setup>
defineProps({
  imageUrl: String,
  title: String,
  price: Number,
  isFavorite: Boolean,
  isAdded: Boolean,
  onClickFavorite: Function,
  onClickAdd: Function,
});
</script>

<template>
  <article
    class="bg-white rounded-3xl p-6 md:p-8 relative border-slate-100 cursor-pointer hover:-translate-y-2 hover:shadow-xl transition duration-300"
  >
    <img
      class="absolute cursor-pointer"
      :src="isFavorite ? '/like-2.svg' : '/like-1.svg'"
      alt="Like"
      @click="onClickFavorite"
    />
    <img class="mb-3" :src="imageUrl" alt="Sneakers" />
    <p class="mb-5">{{ title }}</p>

    <div class="flex justify-between items-center">
      <div class="flex flex-col">
        <span class="text-gray-400">Ціна:</span>
        <b>{{ price }} ₴</b>
      </div>

      <img
        class="cursor-pointer"
        :src="isAdded ? '/checked.svg' : '/plus.svg'"
        alt="Add"
        @click="onClickAdd"
      />
    </div>
  </article>
</template>
