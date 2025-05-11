<template>
  <div class="gap-4 flex items-center border border-slate-300 p-2 rounded-2xl">
    <div class="w-40">
      <img :src="imageSrc" alt="" srcset="">
    </div>
    <div>
      <p>{{ title }}</p>
      <p class="font-bold mt-3">{{ price }} руб.</p>
    </div>
    <div>
      <img class="w-12" src="./../../../public/close.svg" alt="" srcset="">
    </div>
  </div>
</template>

<script setup>

</script>

<style>

</style>