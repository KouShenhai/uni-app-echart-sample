<template>
	<view style="height: 750rpx">
		<l-echart ref="chart"></l-echart>
	</view>
</template>

<script>
	import * as echarts from 'echarts';
	export default {
		data() {
			return {
			}
		},
		async mounted() {
			this.$refs.chart.init(echarts, chart=> {
				var option = {
				    backgroundColor: "#ffffff",
				    tooltip: {
				      trigger: 'item',
				      formatter: "{a}\n{b} : {c}%"
				    },
				    legend: {
				      orient: 'vertical',
				      left: 10,
				      data: ['展现', '点击', '访问', '咨询', '订单']
				    },
				    calculable: true,
				    series: [
				      {
				        name: '漏斗图',
				        type: 'funnel',
				        width: '40%',
				        height: '45%',
				        left: '5%',
				        top: '50%',
				        data: [{ value: 100, name: '展现' },
				        { value: 80, name: '点击' },
				        { value: 60, name: '访问' },
				        { value: 30, name: '咨询' },
				        { value: 10, name: '订单' },
				
				        ]
				      },
				      {
				        name: '金字塔',
				        type: 'funnel',
				        width: '40%',
				        height: '45%',
				        left: '5%',
				        top: '5%',
				        sort: 'ascending',
				        data: [
				          { value: 60, name: '访问' },
				          { value: 30, name: '咨询' },
				          { value: 10, name: '订单' },
				          { value: 80, name: '点击' },
				          { value: 100, name: '展现' }
				        ]
				      },
				      {
				        name: '漏斗图',
				        type: 'funnel',
				        width: '40%',
				        height: '45%',
				        left: '55%',
				        top: '5%',
				        label: {
				          normal: {
				            position: 'left'
				          }
				        },
				        data: [
				          { value: 60, name: '访问' },
				          { value: 30, name: '咨询' },
				          { value: 10, name: '订单' },
				          { value: 80, name: '点击' },
				          { value: 100, name: '展现' }
				        ]
				      },
				      {
				        name: '金字塔',
				        type: 'funnel',
				        width: '40%',
				        height: '45%',
				        left: '55%',
				        top: '50%',
				        sort: 'ascending',
				        label: {
				          normal: {
				            position: 'left'
				          }
				        },
				        data: [
				          { value: 60, name: '访问' },
				          { value: 30, name: '咨询' },
				          { value: 10, name: '订单' },
				          { value: 80, name: '点击' },
				          { value: 100, name: '展现' }
				        ]
				      }
				    ]
				  };
				chart.setOption(option)
				
			});
		},
	}
</script>