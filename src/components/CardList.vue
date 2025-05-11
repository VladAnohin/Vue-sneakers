/<template>
   <div class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-5">
    <Card 
      v-for="item in items"
      :key="item.id"
      :title="item.title"
      :price="item.price"
      :image-url="item.imageUrl"
      :is-favourite="item.isFavourite"
      :is-added="item.isAdded"
      @toggle-favourite="$emit('toggle-favourite', item.id)"
      @toggle-add="$emit('toggle-add', item.id)"
    />
  </div>
</template>

<script setup>
import Card from './Card.vue';
defineProps({
  items: Array,

})

defineEmits(['toggle-favourite', 'toggle-add']);
</script>

<style>

</style>