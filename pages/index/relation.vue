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
				let option = {
					tooltip: {},
					animationDurationUpdate: 1500,
					animationEasingUpdate: 'quinticInOut',
					series: [
						{
							type: 'graph',
							layout: 'none',
							symbolSize: 50,
							roam: true,
							label: {
								show: true
							},
							edgeSymbol: ['circle', 'arrow'],
							edgeSymbolSize: [4, 10],
							edgeLabel: {
								fontSize: 20
							},
							data: [{
								name: '节点1',
								x: 300,
								y: 300
							}, {
								name: '节点2',
								x: 800,
								y: 300
							}, {
								name: '节点3',
								x: 550,
								y: 100
							}, {
								name: '节点4',
								x: 550,
								y: 500
							}],
							// links: [],
							links: [{
								source: 0,
								target: 1,
								symbolSize: [5, 20],
								label: {
									show: true
								},
								lineStyle: {
									width: 5,
									curveness: 0.2
								}
							}, {
								source: '节点2',
								target: '节点1',
								label: {
									show: true
								},
								lineStyle: {
									curveness: 0.2
								}
							}, {
								source: '节点1',
								target: '节点3'
							}, {
								source: '节点2',
								target: '节点3'
							}, {
								source: '节点2',
								target: '节点4'
							}, {
								source: '节点1',
								target: '节点4'
							}],
							lineStyle: {
								opacity: 0.9,
								width: 2,
								curveness: 0
							}
						}
					]
				}
				chart.setOption(option)
				
			});
		},
	}
</script>