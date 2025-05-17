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
