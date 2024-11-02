<script setup>
import Card from './Card.vue';

defineProps({
  items: Array,
});

const onClickFavorite = () => {
  console.log('Favorite');
};

const onClickAdd = () => {
  console.log('Add');
};
</script>

<template>
  <div class="grid grid-cols-4 gap-5">
    <Card
      v-for="item in items"
      :key="item.id"
      :imageURL="item.imageUrl"
      :title="item.title"
      :price="item.price"
      :isFavorite="true"
      :isAdded="true"
      :onClickFavorite="onClickFavorite"
      :onClickAdd="onClickAdd"
    />
  </div>
</template>
