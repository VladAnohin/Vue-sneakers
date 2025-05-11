<template>
  <div>
    <div class="bg-white m-4 relative border border-slate-100 rounded-3xl p-2 cursor-pointer hover:-translate-y-2 transition duration-400 hover:shadow-2xl hover:shadow-gray">
      
      <button @click="toggleFavourite" class="absolute cursor-pointer">
        <img :src="!isFavourite ? '/like-1.svg' : '/like-2.svg'" alt="like" srcset="">

      </button>
      <img :src="imageUrl" alt="Sneakers" srcset="">
      <p>{{ title }}</p>

      <div class="flex justify-between">
        <div class="flex flex-col">
          <span>Цена:</span>
          <span>
         <b>{{ price }}</b> руб.
          </span>
        </div>
        <button @click="toggleAdd" class="cursor-pointer">
          <img :src="!isAdded ? '/plus.svg' : '/checked.svg' " alt="Plus" srcset="">
        </button>
      </div>
    </div>
  </div>
</template>

<script setup>
const props = defineProps({
  imageUrl: String,
  title: String,
  price: Number,
  isFavourite: Boolean,
  isAdded: Boolean
});

const emit = defineEmits(['toggle-favourite', 'toggle-add']);

const toggleFavourite = () => {
  emit('toggle-favourite');
};

const toggleAdd = () => {
  emit('toggle-add');
};
</script>

<style>

</style>