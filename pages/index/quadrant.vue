<template>
  <view style="height: 750rpx">
    <lEchart ref="chartRef"></lEchart>
  </view>
</template>

<script setup>
import { ref, onMounted } from 'vue';
import * as echarts from 'echarts';
import ecStat from 'echarts-stat';
import lEchart from '@/uni_modules/lime-echart/components/l-echart/l-echart.vue';

const chartRef = ref(null);

onMounted(() => {
  // 确保组件已经挂载
  setTimeout(() => {
    if (!chartRef.value) return;
    
    chartRef.value.init(echarts, (chart) => {
      echarts.registerTransform(ecStat.transform.clustering);
      
      const data = [/* 保持原有数据不变 */];
      
      const CLUSTER_COUNT = 6;
      const DIENSIION_CLUSTER_INDEX = 2;
      const COLOR_ALL = [
        '#37A2DA', '#e06343', '#37a354', '#b55dba', '#b5bd48', '#8378EA', '#96BFFF'
      ];
      
      const pieces = Array.from({ length: CLUSTER_COUNT }, (_, i) => ({
        value: i,
        label: `cluster ${i}`,
        color: COLOR_ALL[i]
      }));

      const option = {
        // 保持原有option配置不变
        dataset: [{
          source: data
        }, {
          transform: {
            type: 'ecStat:clustering',
            config: {
              clusterCount: CLUSTER_COUNT,
              outputType: 'single',
              outputClusterIndexDimension: DIENSIION_CLUSTER_INDEX
            }
          }
        }],
        tooltip: {
          position: 'top'
        },
        visualMap: {
          type: 'piecewise',
          top: 'middle',
          min: 0,
          max: CLUSTER_COUNT,
          left: 10,
          splitNumber: CLUSTER_COUNT,
          dimension: DIENSIION_CLUSTER_INDEX,
          pieces: pieces
        },
        grid: {
          left: 120
        },
        xAxis: {},
        yAxis: {},
        series: {
          type: 'scatter',
          encode: { tooltip: [0, 1] },
          symbolSize: 15,
          itemStyle: {
            borderColor: '#555'
          },
          datasetIndex: 1
        }
      };

      chart.setOption(option);
    });
  }, 50); // 添加短暂延迟确保组件初始化完成
});
</script>