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
  // 使用 nextTick 确保组件已经渲染
  setTimeout(() => { // 部分uniapp环境可能需要使用setTimeout替代nextTick
    if (!chartRef.value) return;
    
    chartRef.value.init(echarts, (chart) => {
      const option = {
        legend: {
          top: 'bottom'
        },
        series: [
          {
            name: '面积模式',
            type: 'pie',
            radius: [15, chart.getWidth() / 4],
            center: ['50%', '50%'],
            roseType: 'area',
            itemStyle: {
              borderRadius: 8
            },
            data: [
              {value: 40, name: 'rose 1'},
              {value: 38, name: 'rose 2'},
              {value: 32, name: 'rose 3'},
              {value: 30, name: 'rose 4'},
              {value: 28, name: 'rose 5'},
              {value: 26, name: 'rose 6'},
              {value: 22, name: 'rose 7'},
              {value: 18, name: 'rose 8'}
            ]
          }
        ]
      };
      chart.setOption(option);
    });
  }, 0);
});
</script>