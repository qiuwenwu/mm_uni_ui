<template>
	<!-- 图片 -->
	<mm_item :url="obj[vm.url]">
		<view class="item_image" :class="css">
			<view class="media">
				<mm_icon :src="obj[vm.image]" :desc="obj[vm.tip]"></mm_icon>
			</view>
			<view class="doc">
				<view class="title" v-html="obj[vm.title]"></view>
				<view class="content" v-html="obj[vm.description]" v-if="obj[vm.description]"></view>
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
