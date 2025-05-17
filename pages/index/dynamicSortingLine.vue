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
const countries = ['Finland', 'France', 'Germany', 'Iceland', 'Norway', 'Poland', 'Russia', 'United Kingdom'];

// 获取数据方法
const getData = () => {
  return new Promise(resolve => {
    uni.request({
      url: 'https://fastly.jsdelivr.net/gh/apache/echarts-website@asf-site/examples/data/asset/data/life-expectancy-table.json',
      success: (res) => {
        setTimeout(() => {
          resolve(res.data);
        }, 2000)
      }
    });
  });
};

onMounted(async () => {
  const _rawData = await getData();
  
  if (!chartRef.value) return;

  chartRef.value.init(echarts, chart => {
    const datasetWithFilters = [];
    const seriesList = [];

    countries.forEach(country => {
      const datasetId = `dataset_${country}`;
      datasetWithFilters.push({
        id: datasetId,
        fromDatasetId: 'dataset_raw',
        transform: {
          type: 'filter',
          config: {
            and: [
              { dimension: 'Year', gte: 1950 },
              { dimension: 'Country', '=': country }
            ]
          }
        }
      });

      seriesList.push({
        type: 'line',
        datasetId: datasetId,
        showSymbol: false,
        name: country,
        endLabel: {
          show: true,
          formatter: (params) => params.value[0]
        },
        labelLayout: {
          moveOverlap: 'shiftY'
        },
        emphasis: {
          focus: 'series'
        },
        encode: {
          x: 'Year',
          y: 'Income',
          label: ['Country', 'Income'],
          itemName: 'Year',
          tooltip: ['Income'],
        }
      });
    });

    const option = {
      animationDuration: 10000,
      dataset: [
        { id: 'dataset_raw', source: _rawData },
        ...datasetWithFilters
      ],
      tooltip: {
        order: 'valueDesc',
        trigger: 'axis'
      },
      xAxis: {
        type: 'category',
        nameLocation: 'middle'
      },
      yAxis: {
        name: 'Income'
      },
      grid: {
        right: 140
      },
      series: seriesList
    };

    chart.setOption(option);
  });
});
</script>