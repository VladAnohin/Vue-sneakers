<template>
  <header class="flex justify-between border-b border-slate-300 px-6 py-5">
        <div class="flex items-center gap-4">
          <img src="/logo.png" alt="Logo" class="w-10"/>
          <div>
            <h2 class="text-xl font-bold uppercase">Vue Sneakers</h2>
            <p class="text-slate-500">Магазин лучших кроссовок</p>
          </div>
        </div>
        <nav>
          <ul class="flex items-center gap-10">
            <li class="flex items-center gap-2 text-gray-500 hover:text-black cursor-pointer">
              <img src="/cart.svg" alt="Cart">
              <b>1205 руб</b>
            </li>
            <li class="flex items-center gap-2 text-gray-500 hover:text-black">
              <img src="/heart.svg" alt="heart">
              <span>Закладки</span>
            </li>
            <li class="flex items-center gap-2 text-gray-500 hover:text-black">
              <img src="/profile.svg" alt="profile">
              <b>Профиль</b>
            </li>
          </ul>
        </nav>
      </header> 
</template>

<script setup>

</script>

<style>

</style>