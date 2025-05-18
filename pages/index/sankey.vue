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
					series: {
						type: 'sankey',
						layout: 'none',
						emphasis: {
							focus: 'adjacency'
						},
						data: [{
							name: 'a'
						}, {
							name: 'b'
						}, {
							name: 'a1'
						}, {
							name: 'a2'
						}, {
							name: 'b1'
						}, {
							name: 'c'
						}],
						links: [{
							source: 'a',
							target: 'a1',
							value: 5
						}, {
							source: 'a',
							target: 'a2',
							value: 3
						}, {
							source: 'b',
							target: 'b1',
							value: 8
						}, {
							source: 'a',
							target: 'b1',
							value: 3
						}, {
							source: 'b1',
							target: 'a1',
							value: 1
						}, {
							source: 'b1',
							target: 'c',
							value: 2
						}]
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