<template>
  <view style="height: 750rpx">
    <lEchart ref="chartRef"></lEchart>
  </view>
</template>

<script setup>
import { ref, onMounted } from 'vue';
import * as echarts from 'echarts';
import lEchart from '@/uni_modules/lime-echart/components/l-echart/l-echart.vue';

const chartRef = ref(null);

onMounted(() => {
  if (!chartRef.value) return;
  
  chartRef.value.init(echarts, (chart) => {
    const option = {
      legend: {},
      tooltip: {},
      dataset: {
        source: [
          ['product', '2015', '2016', '2017'],
          ['Matcha Latte', 43.3, 85.8, 93.7],
          ['Milk Tea', 83.1, 73.4, 55.1],
          ['Cheese Cocoa', 86.4, 65.2, 82.5],
          ['Walnut Brownie', 72.4, 53.9, 39.1]
        ]
      },
      xAxis: { type: 'category' },
      yAxis: {},
      series: [
        { type: 'bar' },
        { type: 'bar' },
        { type: 'bar' }
      ]
    };
    chart.setOption(option);
  });
});
</script>