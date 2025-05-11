<template>
    <div class="absolute">
      <!-- <Drawer /> -->
      <div class="w-85/90 m-auto bg-lime-100 h-full rounded-xl shadow-xl mt-14 h-auto p-5 overflow-hidden">
        <Header />
        <div class="p-10">
          <div class="flex justify-between items-center">
            <h2 class="uppercase text-3xl font-bold">Все кроссовки</h2>
        
            <div class="flex gap-3">
              <select @change="onChangeSelect" class="py-2 px-3 border rounded-md outline-none border-gray-300">
                <option value="name">По названию</option>
                <option value="price">По цене(сначала дешёвые)</option>
                <option value="-price">По цене(сначала дорогие)</option>
              </select>
              
                <div class="relative">
                  <img class="absolute left-4 top-3" src="./../../public/search.svg" alt="" srcset="">
                  <input v-model="searchQuery" @input="onChangeSearch" class="bg-white rounded-md py-2 pl-12 pr-4 border border-gray-300 outline-none focus:border-gray-400" type="text" placeholder="Поиск" />
    
                </div>
            </div>
          </div>
        </div>
        <CardList :items="items" @toggle-favourite="toggleFavourite"
        @toggle-add="toggleAdd"/>
     
      </div>
    </div>  
  </template>
  
  <script setup>
  import { onMounted, ref, watch } from 'vue';
  import CardList from './CardList.vue';
  import Drawer from './Drawer/Drawer.vue';
  import Header from './Header.vue';
  import axios from 'axios';

  // ref превращает обычную переменную в реактивную, т.е эту переменную vue начинает отслеживать на изменения
 
  const items = ref([]); // здесь массив товаров
  const isLoading = ref(false); // Флаг загрузки (false/true)
  const sortBy = ref(''); // Параметр сортировки
  const searchQuery = ref(''); // Здесь хранится текст поискового запроса
  let timeoutId = null; // ID таймера для debounce


  const toggleFavourite = id => {
    const item = items.value.find(item => item.id === id);
    if (item) {
      item.isFavourite = !item.isFavourite;
    } 
  };
  const toggleAdd = id => {
    const item = items.value.find(item => item.id === id);
    if (item) {
      item.isAdded = !item.isAdded;
    }
  };
  const fetchItems = async () => {
  try {
    isLoading.value = true; //здесь отображается загрузка в консоли
    
    const params = {}; // объект параметров для апи

    if(sortBy.value){ // если выбрана сортировка
      params.sortBy = sortBy.value;
    };
    if(searchQuery.value) { // если есть поисковый запрос
      params.title = `*${searchQuery.value}*` //ищем по подстроке
    }
    const { data } = await axios.get('https://604781a0efa572c1.mokky.dev/items', {params}); // дефолтный гет-запрос с параметрами. Гет-запрос как бы "собирает" данные с сервера и отдает эти данные сайту. По сути здесь мы обновляем данные каждый раз
    items.value = data.map(item => ({
      ...item,
      isFavourite: item.isFavourite || false,
      isAdded: item.isAdded || false
    }));
  }
  catch(err){ // здесь просто выводится ошибка при неудачной загрузке страницы
    console.error('Ошибка при загрузке:', err);

  }
  finally {
    isLoading.value = false; // если загрузилась страница, скрываем индикатор загрузки
  }
 }
 const debouncedFetch = () => {
  clearTimeout(timeoutId); // отменяет предыдущий запрос, если он не успел выполнится
  timeoutId = setTimeout(fetchItems, 500); // запускает fetchItems через 500мс после последнего ввода
 }
 const onChangeSelect = event => { // срабатывает при выборе сортировки
  sortBy.value = event.target.value; // обновляем параметр сортировки
 };
 const onChangeSearch = event => { // аналогично с сортировкой, только это поиск
  searchQuery.value = event.target.value;
 };
 watch([sortBy, searchQuery], () => { // следит за изменениями в sortBy и searchQuery
  debouncedFetch(); // вызывает функцию с задержкой
 })
 onMounted(() => {
  debouncedFetch(); // загрузка данных при первом рендере
 })


 // Debounce - это паттерн, который позволяет сократить большое количество запросов на сервер, например, от того же инпута, с условных 30 запросов до 1. Путем создания setTimeout/clearTimeout 500ms.
  </script>
  
  <style>
  
  </style>
