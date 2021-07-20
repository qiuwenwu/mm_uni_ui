<template>
	<!-- 常见问题 -->
	<mm_item :url="obj[vm.url]">
		<view class="item_question" :class="css">
			<view class="doc">
				<view class="time" v-if="obj[vm.time]"><text>{{$to_time(obj[vm.time])}}</text></view>
				<view class="title" v-if="obj[vm.title]"><text>{{obj[vm.title]}}</text></view>
				<view class="content" v-if="obj[vm.description]"><text>{{obj[vm.description]}}</text></view>
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
