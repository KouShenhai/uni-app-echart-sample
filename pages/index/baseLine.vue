<template>
  <view style="height: 750rpx">
    <lEchart ref="chartRef"></lEchart >
  </view>
</template>

<script setup>
import { ref, onMounted } from 'vue';
import lEchart from '@/uni_modules/lime-echart/components/l-echart/l-echart.vue';
import * as echarts from "echarts";

// 图表配置项
const option = ref({
  xAxis: {
    type: 'category',
    data: ['Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat', 'Sun']
  },
  yAxis: {
    type: 'value'
  },
  series: [{
    data: [150, 230, 224, 218, 135, 147, 260],
    type: 'line'
  }]
});

// 图表引用
const chartRef = ref(null);

onMounted(() => {
  // 确保组件已经挂载后再初始化图表
  if (chartRef.value) {
    chartRef.value.init(echarts, (chart) => {
      chart.setOption(option.value);
    });
  }
});
</script>