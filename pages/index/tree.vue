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
				var data1 = {
					name: 'root',
					children: [
						{
							name: 'a',
							children: [
								{
									name: 'a1'
								},
								{
									name: 'a2'
								},
								{
									name: 'a3'
								},
								{
									name: 'a4'
								}
							]
						},
						{
							name: 'b',
							children: [
								{
									name: 'b1'
								},
								{
									name: 'b2'
								},
								{
									name: 'b3'
								},
								{
									name: 'b4'
								}
							]
						},
						{
							name: 'c',
							children: [
								{
									name: 'c1'
								}
							]
						},
						{
							name: 'd',
							children: [
								{
									name: 'd1'
								}
							]
						}
					]
				};

				var option = {
					series: [
						{
							type: 'tree',

							initialTreeDepth: -1,

							name: 'tree1',

							data: [data1],

							top: '5%',
							left: '20%',
							bottom: '2%',
							right: '15%',

							symbolSize: 10,
							symbol: 'circle',

							label: {
								normal: {
									position: 'left',
									verticalAlign: 'middle',
									align: 'right',
									color: 'black'
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