<template>
    <div class="fixed top-0 left-0 w-full h-full bg-black z-10 opacity-70"></div>
    <div class="bg-white h-full fixed right-0 top-0 w-3/10 z-20 p-10" >
       <DrawerHead />
      <CardListDrawer />
       <div class="flex flex-col gap-4 my-6">
        <div class="flex gap-2">
            <span>Итого:</span>
            <div class="flex-1 border-b border-dashed"></div>
            <b>21999 руб.</b>
        </div>
        <div class="flex gap-2">
            <span>Налог 5%:</span>
            <div class="flex-1 border-b border-dashed"></div>
            <b>900 р.</b>
        </div>
        <button disabled class="bg-lime-500 w-full rounded-xl py-3 mt-5 text-white cursor-pointer hover:bg-lime-600 focus:bg-lime-700 transition disabled:bg-slate-300">
            Оформить заказ
        </button>
       </div>
  </div>
</template>

<script setup>
import CardListDrawer from './CardListDrawer.vue';
import DrawerHead from './DrawerHead.vue';
</script>

<style>

</style>