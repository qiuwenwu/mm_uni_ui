<template>
	<!-- 新闻 -->
	<mm_item :url="obj[vm.url]">
		<view class="item_news" :class="css">
			<view class="media" v-if="!obj[vm.imgs] || !(obj[vm.imgs].length>1)">
				<mm_icon :src="obj[vm.image]" :desc="obj[vm.tip]"></mm_icon>
			</view>
			<view class="doc">
				<view class="title" v-if="obj[vm.title]"><text>{{obj[vm.title]}}</text></view>
				<view class="content" v-if="obj[vm.description]"><text>{{obj[vm.description]}}</text></view>
				<view class="imgs" v-if="obj[vm.imgs] && obj[vm.imgs].length>1">
					<view v-for="(o,i) in obj[vm.imgs]" :key="i">
						<image class="img" :src="o" alt="">
					</view>
				</view>
				<view class="info">
					<view class="source" v-if="obj[vm.source]"><text>{{obj[vm.source]}}</text></view>
					<view class="author" v-if="obj[vm.author]"><text>{{obj[vm.author]}}</text></view>
					<view class="tag" v-if="obj[vm.tag]"><text>{{obj[vm.tag]}}</text></view>
					<view class="time" v-if="obj[vm.create_time]"><text>{{ $to_time(obj[vm.create_time]) }}</text></view>
				</view>
			</view>
		</view>
	</mm_item>
</template>

<script>
	import mixin from '@/mixins/item.js'

	export default {
		mixins: [mixin]
	}
</script>

<style>

</style>
