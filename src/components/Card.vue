<script setup>
defineProps({
  imageURL: String,
  title: String,
  price: Number,
  isFavorite: Boolean,
  isAdded: Boolean,
  onClickFavorite: Function,
  onClickAdd: Function,
});
</script>

<template>
  <div>
    <div
      class="relative bg-white border border-slate-100 rounded-3xl p-8 cursor-pointer transition hover:-translate-y-2 hover:shadow-xl"
    >
      <img
        class="absolute top-8 left-8"
        :src="isFavorite ? '/like-2.svg' : '/like-1.svg'"
        :alt="isFavorite ? 'Like active' : 'Like disabled'"
        @click="onClickFavorite"
      />
      <img :src="imageURL" alt="Sneaker" />
      <p class="mt-5">{{ title }}</p>

      <div class="flex justify-between mt-5">
        <div class="flex flex-col">
          <span class="text-slate-400">Ціна:</span>
          <b>{{ price }} ₴</b>
        </div>
        <img
          :src="!isAdded ? '/plus.svg' : '/checked.svg'"
          :alt="isAdded ? 'Plus' : 'Checked'"
          @click="onClickAdd"
        />
      </div>
    </div>
  </div>
</template>
