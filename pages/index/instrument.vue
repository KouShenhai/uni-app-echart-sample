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
				    series: [{
				      name: '业务指标',
				      type: 'gauge',
				      detail: {
				        formatter: '{value}%'
				      },
				      axisLine: {
				        show: true
				      },
				      data: [{
				        value: 40,
				        name: '完成率',
				      }]
				
				    }]
				  };
				chart.setOption(option)
				
			});
		},
	}
</script>