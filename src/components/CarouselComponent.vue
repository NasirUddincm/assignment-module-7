<script setup>
import {ref, onMounted, onBeforeUnmount} from 'vue'

const items = ref([
  'https://images.unsplash.com/photo-1690149347325-13435f400dd9?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=650&q=80',
  'https://plus.unsplash.com/premium_photo-1691588961574-0387cf9a3834?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=650&q=80',
  'https://images.unsplash.com/photo-1691425938881-2cac802cf078?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=650&q=80',
  'https://images.unsplash.com/photo-1691319843283-24e1d9eeacab?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w650&q=80'
])
let carousel = null

onMounted(() => {
  carousel = new Flickity('#carousel',{
    autoPlay: 3000, // Autoplay interval in milliseconds
  })
})

onBeforeUnmount(() => {
  if (carousel) {
    carousel.destroy(); //carousel is cleanup when component is unmounted
  }
});

</script>
<template>  
  <div class="mx-auto items" id="carousel">
    <div :style="`background-image:url(${item})`" class="item" v-for="(item, index) in items" :key="index"></div>
  </div>
</template>
<style scoped>
.items{
  width: 600px;
  height: 400px;
}
.item{
  width: 600px;
  height: 400px;
  background-color: #ccc;
  background-size: cover;
}

</style>