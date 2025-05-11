/<template>
  <div class='grid gap-4'>
    <CardDrawer imageSrc="./sneakers/sneakers-2.jpg" :price="12999" title="Мужские кроссовки Nike Air Max 270"/>
    <CardDrawer imageSrc="./sneakers/sneakers-4.jpg" :price="8999" title="Кроссовки Puma X Aka Boku Future Rider"/>
  </div>
</template>

<script setup>
import CardDrawer from './CardDrawer.vue';
defineProps({
  imageSrc: String,
  price: Number,
  title: String,
})
</script>

<style>

</style>