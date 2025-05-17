<template>
  <view style="height: 750rpx">
    <lEchart ref="chartRef"></lEchart>
  </view>
</template>

<script setup>
import { ref, onMounted, onUnmounted, shallowRef } from 'vue'
import * as echarts from 'echarts'
import lEchart from '@/uni_modules/lime-echart/components/l-echart/l-echart.vue';

const chartRef = ref(null)
let timer = null
const count = ref(11)

// 使用 shallowRef 避免深层响应式（性能优化）
const option = shallowRef({
  tooltip: {
    trigger: 'axis',
    axisPointer: {
      type: 'cross',
      label: {
        backgroundColor: '#283b56'
      }
    }
  },
  legend: {
    data: ['最新成交价', '预购队列']
  },
  dataZoom: {
    show: false,
    start: 0,
    end: 100
  },
  xAxis: [
    {
      type: 'category',
      boundaryGap: true,
      data: generateTimeData()
    },
    {
      type: 'category',
      boundaryGap: true,
      data: generateIndexData()
    }
  ],
  yAxis: [
    {
      type: 'value',
      scale: true,
      name: '价格',
      max: 30,
      min: 0,
      boundaryGap: [0.2, 0.2]
    },
    {
      type: 'value',
      scale: true,
      name: '预购量',
      max: 1200,
      min: 0,
      boundaryGap: [0.2, 0.2]
    }
  ],
  series: [
    {
      name: '预购队列',
      type: 'bar',
      xAxisIndex: 1,
      yAxisIndex: 1,
      data: generateRandomData(10, 1000)
    },
    {
      name: '最新成交价',
      type: 'line',
      data: generateRandomFloatData(10, 5, 10)
    }
  ]
})

// 生成时间数据
function generateTimeData() {
  const now = new Date()
  return Array.from({ length: 10 }, (_, i) => {
    const time = new Date(now - (10 - i - 1) * 2000)
    return time.toLocaleTimeString().replace(/^\D*/, '')
  })
}

// 生成索引数据
function generateIndexData() {
  return Array.from({ length: 10 }, (_, i) => i)
}

// 生成随机整数数据
function generateRandomData(length, max) {
  return Array.from({ length }, () => Math.round(Math.random() * max))
}

// 生成随机浮点数数据
function generateRandomFloatData(length, base, range) {
  return Array.from({ length }, () => Number((Math.random() * range + base).toFixed(1)))
}

onMounted(() => {
  // 初始化图表
  chartRef.value.init(echarts, chart => {
    chart.setOption(option.value)
    
    // 定时更新数据
    timer = setInterval(() => {
      const axisData = new Date().toLocaleTimeString().replace(/^\D*/, '')
      
      const newOption = { ...option.value }
      newOption.xAxis[0].data = [...newOption.xAxis[0].data.slice(1), axisData]
      newOption.xAxis[1].data = [...newOption.xAxis[1].data.slice(1), count.value++]
      
      newOption.series[0].data = [...newOption.series[0].data.slice(1), Math.round(Math.random() * 1000)]
      newOption.series[1].data = [...newOption.series[1].data.slice(1), Number((Math.random() * 10 + 5).toFixed(1))]
      
      option.value = newOption
      chart.setOption(option.value)
    }, 2100)
  })
})

onUnmounted(() => {
  // 清除定时器
  if (timer) clearInterval(timer)
})
</script>