<script setup>
import CardItem from './CardItem.vue';

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
      imageUrl="/sneakers/sneakers-1.jpg"
      title="Чоловічі кросівки Nike Blazer Mid Suede"
      :price="3000"
      :isFavorite="true"
      :isAdded="true"
      :onClickFavorite="onClickFavorite"
      :onClickAdd="onClickAdd"
    />
    <CardItem
      imageUrl="/sneakers/sneakers-2.jpg"
      title="Чоловічі кросівки Nike Blazer Mid Suede"
      :price="3000"
      :isFavorite="false"
      :isAdded="true"
    />
    <CardItem
      imageUrl="/sneakers/sneakers-3.jpg"
      title="Чоловічі кросівки Nike Blazer Mid Suede"
      :price="3000"
    />
    <CardItem
      imageUrl="/sneakers/sneakers-4.jpg"
      title="Чоловічі кросівки Nike Blazer Mid Suede"
      :price="3000"
    />
    <CardItem
      imageUrl="/sneakers/sneakers-5.jpg"
      title="Чоловічі кросівки Nike Blazer Mid Suede"
      :price="3000"
    />
    <CardItem
      imageUrl="/sneakers/sneakers-6.jpg"
      title="Чоловічі кросівки Nike Blazer Mid Suede"
      :price="3000"
    />
    <CardItem
      imageUrl="/sneakers/sneakers-7.jpg"
      title="Чоловічі кросівки Nike Blazer Mid Suede"
      :price="3000"
    />
  </section>
</template>
