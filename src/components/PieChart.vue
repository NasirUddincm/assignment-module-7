<script setup>
import { onMounted, onBeforeUnmount } from 'vue';

let chart = null;
const dataset = [300, 50, 100];

const data = {
  labels: ['Red', 'Blue', 'Yellow'],
  datasets: [
    {
      label: 'My First Dataset',
      data: dataset,
      backgroundColor: ['rgb(255, 99, 132)', 'rgb(54, 162, 235)', 'rgb(255, 205, 86)'],
      hoverOffset: 4,
    },
  ],
};
const config = {
  type: 'pie',
  data: data,
};

onMounted(() => {
  const ctx = document.getElementById('myChart');
  chart = new Chart(ctx, config);
});

onBeforeUnmount(() => {
  // Cleanup chart instance when the component is unmounted
  if (chart) {
    chart.destroy();
  }
});

</script>
<template>
  <div class="mx-auto w-[400px] h-[400px] bg-gray-400">
    <canvas id="myChart"></canvas>
  </div>  
</template>