<template>
  <view style="height: 750rpx">
    <l-echart ref="chart"></l-echart>
  </view>
</template>

<script>
import * as echarts from 'echarts';
export default {
  data() {
    return {}
  },
  async mounted() {
    this.$refs.chart.init(echarts, chart=> {
      const model = {
        yCates: ['Saturday', 'Friday', 'Thursday', 'Wednesday', 'Tuesday', 'Monday', 'Sunday'],
        xCates: ['1', '2', '3', '4', '5'],
        data: [
          // [yCateIndex, xCateIndex, value]
          [0, 0, 5],
          [0, 1, 7],
          [0, 2, 3],
          [0, 3, 5],
          [0, 4, 2],
          [1, 0, 1],
          [1, 1, 2],
          [1, 2, 4],
          [1, 3, 8],
          [1, 4, 2],
          [2, 0, 2],
          [2, 1, 3],
          [2, 2, 8],
          [2, 3, 6],
          [2, 4, 7],
          [3, 0, 3],
          [3, 1, 7],
          [3, 2, 5],
          [3, 3, 1],
          [3, 4, 6],
          [4, 0, 3],
          [4, 1, 2],
          [4, 2, 7],
          [4, 3, 8],
          [4, 4, 9],
          [5, 0, 2],
          [5, 1, 2],
          [5, 2, 3],
          [5, 3, 4],
          [5, 4, 7],
          [6, 0, 6],
          [6, 1, 5],
          [6, 2, 3],
          [6, 3, 1],
          [6, 4, 2]
        ]
      };

      const data = model.data.map(function(item) {
        return [item[1], item[0], item[2] || '-'];
      });

      const option = {
        tooltip: {
          position: 'top'
        },
        animation: false,
        grid: {
          bottom: 60,
          top: 10,
          left: 80
        },
        xAxis: {
          type: 'category',
          data: model.xCates
        },
        yAxis: {
          type: 'category',
          data: model.yCates
        },
        visualMap: {
          min: 1,
          max: 10,
          show: false,
          calculable: true,
          orient: 'horizontal',
          left: 'center',
          bottom: 10,
          inRange: {
            color: ['#37A2DA', '#32C5E9', '#67E0E3', '#91F2DE', '#FFDB5C', '#FF9F7F']
          }
        },
        series: [
          {
            name: 'Punch Card',
            type: 'heatmap',
            data: data,
            label: {
              normal: {
                show: true
              }
            },
            itemStyle: {
              emphasis: {
                shadowBlur: 10,
                shadowColor: 'rgba(0, 0, 0, 0.5)'
              }
            }
          }
        ]
      };
      chart.setOption(option)

    });
  },
}
</script>