<template>
  <view style="height: 750rpx">
    <lEchart ref="chartRef"></lEchart>
  </view>
</template>

<script setup>
import { ref, onMounted } from 'vue';
import lEchart from '@/uni_modules/lime-echart/components/l-echart/l-echart.vue';
import * as echarts from 'echarts';

const chartRef = ref(null);

const option = {
  title: {
    text: '深圳月最低生活费组成（单位:元）',
    subtext: 'From ExcelHome',
    sublink: 'http://e.weibo.com/1341556070/AjQH99che'
  },
  tooltip: {
    trigger: 'axis',
    axisPointer: {
      type: 'shadow'
    },
    formatter: (params) => {
      const tar = params[1];
      return `${tar.name}<br/>${tar.seriesName} : ${tar.value}`;
    }
  },
  grid: {
    left: '3%',
    right: '4%',
    bottom: '3%',
    containLabel: true
  },
  xAxis: {
    type: 'category',
    splitLine: { show: false },
    data: ['总费用', '房租', '水电费', '交通费', '伙食费', '日用品数']
  },
  yAxis: {
    type: 'value'
  },
  series: [
    {
      name: '辅助',
      type: 'bar',
      stack: '总量',
      itemStyle: {
        barBorderColor: 'rgba(0,0,0,0)',
        color: 'rgba(0,0,0,0)'
      },
      emphasis: {
        itemStyle: {
          barBorderColor: 'rgba(0,0,0,0)',
          color: 'rgba(0,0,0,0)'
        }
      },
      data: [0, 1700, 1400, 1200, 300, 0]
    },
    {
      name: '生活费',
      type: 'bar',
      stack: '总量',
      label: {
        show: true,
        position: 'inside'
      },
      data: [2900, 1200, 300, 200, 900, 300]
    }
  ]
};

onMounted(() => {
  chartRef.value.init(echarts, chart => {
    chart.setOption(option);
  });
});
</script>