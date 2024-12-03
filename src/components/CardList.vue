<script setup>
import CardItem from './CardItem.vue';

defineProps({
  items: Array,
});

const onClickFavorite = () => {
  alert('favorite');
};

const onClickAdd = () => {
  alert('add');
};
</script>

<template>
  <section class="grid sm:grid-cols-2 lg:grid-cols-3 xl:grid-cols-4 gap-5">
    <CardItem
      v-for="item in items"
      :key="item.id"
      :imageUrl="item.imageUrl"
      :title="item.title"
      :price="item.price"
      :isFavorite="false"
      :isAdded="false"
      :onClickFavorite="onClickFavorite"
      :onClickAdd="onClickAdd"
    />
  </section>
</template>
