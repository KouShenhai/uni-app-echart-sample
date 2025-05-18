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
				option : {
					series: [{
						type: 'gauge',
						startAngle: 90,
						endAngle: -270,
						pointer: {
							show: false
						},
						progress: {
							show: true,
							overlap: false,
							roundCap: true,
							clip: false,
							itemStyle: {
								// borderWidth: 1,
								// borderColor: '#464646'
							}
						},
						axisLine: {

							lineStyle: {
								width: 40
							}
						},
						splitLine: {
							show: false,
							distance: 0,
							length: 10
						},
						axisTick: {
							show: false
						},
						axisLabel: {
							show: false,
							distance: 50
						},
						data: [
							{
							value: 20,
							detail: {
							offsetCenter: ['0%', '0%']
							}
						}
						],
						detail: {
							// width: 50,
							// height: 14,
							fontSize: 34,
							//color: 'auto',
							// borderColor: 'auto',
							// borderRadius: 20,
							// borderWidth: 1,
							formatter: '{value}%'
						}
					}]
				}
			}
		},
		async mounted() {
			this.$refs.chart.init(echarts, chart=> {
				chart.setOption(this.option)
				setInterval(() => {
					this.option.series[0].pointer.show = false;
					this.option.series[0].data[0].value = (Math.random() * 100).toFixed(2) - 0;
					chart.setOption(this.option, true);
				}, 2000);
				
			});
		},
	}
</script>