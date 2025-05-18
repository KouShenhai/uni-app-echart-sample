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
				option: {
					parallelAxis: [
						{dim: 0, name: 'Price'},
						{dim: 1, name: 'Net Weight'},
						{dim: 2, name: 'Amount'},
						{
							dim: 3,
							name: 'Score',
							type: 'category',
							data: ['Excellent', 'Good', 'OK', 'Bad']
						}
					],
					series: {
						type: 'parallel',
						lineStyle: {
							width: 4
						},
						data: [
							[12.99, 100, 82, 'Good'],
							[9.99, 80, 77, 'OK'],
							[20, 120, 60, 'Excellent']
						]
					}
				}
			}
		},
		async mounted() {
			this.$refs.chart.init(echarts, chart=> {
				chart.setOption(this.option)
				
			});
		},
	}
</script>