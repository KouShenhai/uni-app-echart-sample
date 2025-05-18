<template>
	<view @click="goTo('/pages/index/baseLine')">基础折线图【查看点击我】</view>
	<view @click="goTo('/pages/index/smoothLine')">平滑折线图【查看点击我】</view>
	<view @click="goTo('/pages/index/stackingLineChart')">折线图堆叠【查看点击我】</view>
	<view @click="goTo('/pages/index/dynamicSortingLine')">动态排序折线图【查看点击我】</view>
	<view @click="goTo('/pages/index/basicArea')">基础面积图【查看点击我】</view>
	<view @click="goTo('/pages/index/stackingArea')">堆叠区域图【查看点击我】</view>
	<view @click="goTo('/pages/index/basicColumnarShape')">基础柱状图【查看点击我】</view>
	<view @click="goTo('/pages/index/basicColumnarShape2')">柱状图坐标轴刻度与标签对齐【查看点击我】</view>
	<view @click="goTo('/pages/index/waterfall')">瀑布图（柱状图模拟）【查看点击我】</view>
	<view @click="goTo('/pages/index/interleaved')">交错正负轴标签【查看点击我】</view>
	<view @click="goTo('/pages/index/bar')">条形图【查看点击我】</view>
	<view @click="goTo('/pages/index/bar2')">条形图【渐变色 阴影 点击 缩放】【查看点击我】</view>
	<view @click="goTo('/pages/index/stackedBar')">堆叠条形图【查看点击我】</view>
	<view @click="goTo('/pages/index/bar3')">正负条形图【查看点击我】</view>
	<view @click="goTo('/pages/index/dynamicData')">动态数据【查看点击我】</view>
	<view @click="goTo('/pages/index/dataSet')">最简单的数据集【查看点击我】</view>
	<view @click="goTo('/pages/index/circular')">环形图【查看点击我】</view>
	<view @click="goTo('/pages/index/pie')">饼图【查看点击我】</view>
	<view @click="goTo('/pages/index/pie2')">基础南丁格尔玫瑰图【查看点击我】</view>
	<view @click="goTo('/pages/index/splashed')">散点图【查看点击我】</view>
	<view @click="goTo('/pages/index/quadrant')">四象限【查看点击我，暂支持Vue2】</view>
	<view @click="goTo('/pages/index/map')">地图【查看点击我】</view>
	<view @click="goTo('/pages/index/k')">K线【查看点击我】</view>
  <view @click="goTo('/pages/index/index2')">上证指数【查看点击我，暂支持Vue2】</view>
  <view @click="goTo('/pages/index/radar')">雷达图【查看点击我】</view>
  <view @click="goTo('/pages/index/box')">盒须图【查看点击我，暂支持Vue2】</view>
  <view @click="goTo('/pages/index/hot')">热力图【查看点击我，暂支持Vue2】</view>
  <view @click="goTo('/pages/index/relation')">关系图【查看点击我，暂支持Vue2】</view>
  <view @click="goTo('/pages/index/tree')">树图【查看点击我，暂支持Vue2】</view>
  <view @click="goTo('/pages/index/tree2')">矩形树图【查看点击我，暂支持Vue2】</view>
  <view @click="goTo('/pages/index/sun')">旭日图【查看点击我，暂支持Vue2】</view>
  <view @click="goTo('/pages/index/coordinate')">平行坐标系【查看点击我，暂支持Vue2】</view>
  <view @click="goTo('/pages/index/sankey')">桑基图【查看点击我，暂支持Vue2】</view>
  <view @click="goTo('/pages/index/funnel')">漏斗图【查看点击我，暂支持Vue2】</view>
  <view @click="goTo('/pages/index/instrument')">仪表盘【查看点击我，暂支持Vue2】</view>
  <view @click="goTo('/pages/index/progress')">进度条【查看点击我，暂支持Vue2】</view>
  <view @click="goTo('/pages/index/river')">主题河流图【查看点击我，暂支持Vue2】</view>
</template>

<script setup>
	const goTo = async(url) => {
		uni.navigateTo({
			url: url
		})
	}
</script>

<style scoped>

</style>
