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
const option = {
  tooltip: {
    trigger: 'axis',
    axisPointer: {
      type: 'shadow'
    }
  },
  legend: {
    data: ['利润', '支出', '收入']
  },
  grid: {
    left: '3%',
    right: '4%',
    bottom: '3%',
    containLabel: true
  },
  xAxis: [
    {
      type: 'value'
    }
  ],
  yAxis: [
    {
      type: 'category',
      axisTick: {
        show: false
      },
      data: ['周一', '周二', '周三', '周四', '周五', '周六', '周日']
    }
  ],
  series: [
    {
      name: '利润',
      type: 'bar',
      label: {
        show: true,
        position: 'inside'
      },
      emphasis: {
        focus: 'series'
      },
      data: [200, 170, 240, 244, 200, 220, 210]
    },
    {
      name: '收入',
      type: 'bar',
      stack: '总量',
      label: {
        show: true
      },
      emphasis: {
        focus: 'series'
      },
      data: [320, 302, 341, 374, 390, 450, 420]
    },
    {
      name: '支出',
      type: 'bar',
      stack: '总量',
      label: {
        show: true,
        position: 'left'
      },
      emphasis: {
        focus: 'series'
      },
      data: [-120, -132, -101, -134, -190, -230, -210]
    }
  ]
};

onMounted(() => {
  if (chartRef.value) {
    chartRef.value.init(echarts, (chart) => {
      chart.setOption(option);
    });
  }
});
</script>